```// Boilerplate: connect to DB
const { MongoClient } = require('mongodb');
const uri = 'mongodb://localhost:27017,localhost:27018,localhost:27019/txn';
const client = await MongoClient.connect(uri, { useNewUrlParser: true, replicaSet: 'rs' });

const db = client.db();
await db.dropDatabase();

// Insert accounts and transfer some money
await db.collection('Account').insertMany([
  { name: 'A', balance: 5 },
  { name: 'B', balance: 10 }
]);

await transfer('A', 'B', 4); // Success
try {
  // Fails because then A would have a negative balance
  await transfer('A', 'B', 2);
} catch (error) {
  error.message; // "Insufficient funds: 1"
}

// The actual transfer logic
async function transfer(from, to, amount) {
  const session = client.startSession();
  session.startTransaction();
  try {
    const opts = { session, returnOriginal: false };
    const A = await db.collection('Account').
      findOneAndUpdate({ name: from }, { $inc: { balance: -amount } }, opts).
      then(res => res.value);
    if (A.balance < 0) {
      // If A would have negative balance, fail and abort the transaction
      // `session.abortTransaction()` will undo the above `findOneAndUpdate()`
      throw new Error('Insufficient funds: ' + (A.balance + amount));
    }

    const B = await db.collection('Account').
      findOneAndUpdate({ name: to }, { $inc: { balance: amount } }, opts).
      then(res => res.value);

    await session.commitTransaction();
    session.endSession();
    return { from: A, to: B };
  } catch (error) {
    // If an error occurred, abort the whole transaction and
    // undo any changes that might have happened
    await session.abortTransaction();
    session.endSession();
    throw error; // Rethrow so calling function sees error
  }
}
```
