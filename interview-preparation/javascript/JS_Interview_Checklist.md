# Important Concepts To Aware:

1. Value and References
2. Scope
3. Hoisting
4. Closures
5. Objects and this, new, apply, call, bind
6. Prototypes and Inheritance
7. Asynchronous JS - Promise, await, async
8. High Order Function, Functional Programming, Pure Function, Currying, Tranpiler, pollyfill

# Questions on Values and References

1. what is the output of below program?

```
var a = 10;

function fun1(val) {
val = 20;
}

fun1(a);
console.log(a);
```

2. what is the output of below program?

```var a = {num : 10};

function fun1(val) {
val.num = 20;
}

fun1(a);
console.log(a);
```

3. what is the output of below program?

```var a = {num : 10};

function fun1(val) {
val= {};
}

fun1(a);
console.log(a);
```

# Questions on Scoping and Hosting

1. what is the output of below program?

`if(false) { var a = 10; } console.log(a);`

2. what is the output of below program?

`console.log(a); if(true) { var a = 10; }`

3. what is the output of below program?

`console.log(a); if(false) { var b = 10; var b = 50; }`

4. what is the output of below program?

`console.log(a); if(false) { let a = 10; }`

`console.log(a); if(false) { let a = 10; let a = 10; }`

5. what is the output of below program?

`function fun1(val) { var a = 10; } console.log(a);`

6. what is the output of below program?

`function fun1(val) { var a = val; } fun1(10) console.log(a);`

7. what is the output of below program?

`const one = 10; one = 20; console.log(one);`

`const obj = { a : 10}; obj.b = 50; console.log(obj);`

`const x = 10; function a() { const x = 20; }`

`const x = 10; function a(x) { const x = 20; } a(10)`

`const x = 10; if(true) { const x = 20; }`

8. what is the output of below program?

`console.log(a); var a = 10; console.log(a);`

`console.log(a); let a = 10; console.log(a);`

9. what is the output of below program?

`console.log(a); var a = 10; console.log(a); function a(){ console.log("Function"); }`

`console.log(a); var a = 10; function a(){ console.log("Function"); } console.log(a);`

10. what is the output of below program?

```
(function(){
var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```

# Questions on Closures

1. what is the output of below program?

```var globalVar = "xyz";

(function outerFunc(outerArg) {
var outerVar = 'a';

    (function innerFunc(innerArg) {
    var innerVar = 'b';

    console.log(
        "outerArg = " + outerArg + "\n" +
        "innerArg = " + innerArg + "\n" +
        "outerVar = " + outerVar + "\n" +
        "innerVar = " + innerVar + "\n" +
        "globalVar = " + globalVar);

    })(456);

})(123);
```

2. what is the output of below program?

```
let a = 10;

function fun1(){
let a = 20;
fun2();
}

function fun2() {
console.log(a);
}
console.dir(fun2);
fun1()

```

```

let a = 10;

function fun1(){
let a = 20;

let b = 20;
function fun2() {
console.log(a+b);
}
console.dir(fun2);
fun2();

}

fun1()

```

```

var a = 10;

function fun1(){
var a = 20;

let b = 20;
function fun2() {
console.log(a+b);
}
console.dir(fun2);
fun2();

}

fun1()

```

3. what is the output of below program?

`for (var i = 0; i < 5; i++) { setTimeout(function(){ console.log(i); }, 1000) }`

4. what is the output of below program?

`(function(x) { return (function(y) { console.log(x); })(2) })(1);`

5. what is the output of below program?

`var x = 21; var girl = function () { console.log(x); var x = 20; }; girl ();`

6. what is the output of below program?

`(function () { try { throw new Error(); } catch (x) { var x = 1, y = 2; console.log(x); } console.log(x); console.log(y); })();`

7. what is the output of below program?

`var b = 1; function outer(){ var b = 2 function inner(){ b++; var b = 3; console.log(b) } inner(); } outer();`

# Common Questions and Object Related

1. what is the output of below program?

`console.log(1 + "2" + "2"); console.log(1 + +"2" + "2"); console.log(1 + -"1" + "2"); console.log(+"1" + "1" + "2"); console.log( "A" - "B" + "2"); console.log( "A" - "B" + 2);`

2. what is the output of below program?

Imagine you have this code:

```
var a = [1, 2, 3];
a) Will this result in a crash?

a[10] = 99;
b) What will this output?

console.log(a[6]);
```

3. what is the output of below program?

`var myObject = { foo: "bar", func: function() { var self = this; console.log("outer func: this.foo = " + this.foo); console.log("outer func: self.foo = " + self.foo); (function() { console.log("inner func: this.foo = " + this.foo); console.log("inner func: self.foo = " + self.foo); }()); } }; myObject.func();`

4. what is the output of below program?

`function foo(val1, val1){ console.log(val1); } foo(10, 20);`

5. what is the output of below program?

```
function foo1()
{
return {
bar: "hello"
};
}

function foo2()
{
return
{
bar: "hello"
};
}
```

6. what is the output of below program?

```
(function() {
console.log(1);
setTimeout(function(){console.log(2)}, 1000);
setTimeout(function(){console.log(3)}, 0);
console.log(4);
})();
```

7. Write a sum method which will work properly when invoked using either syntax below.

```
console.log(sum(2,3)); // Outputs 5 console.log(sum(2)(3)); // Outputs 5
```

8. what is the output of below program?

```
var a={},
b={key:'b'},
c={key:'c'};

a[b]=123;
a[c]=456;

console.log(a[b]);
```

9. what is the output of below program?

```
var hero = {
name: 'John Doe',
getSecretIdentity: function (){
return this.name;
}
};

var stoleSecretIdentity = hero.getSecretIdentity;

console.log(stoleSecretIdentity());
console.log(hero.getSecretIdentity());
```

# Common Things to remember!!!

1. What is the difference between two-way data binding and one way data binding?
2. what is type coercion?
3. what is functional programming?
4. What is IIFE? Array Destructuring, Spread Operator, Rest Operator, eval(), Usage of 'use strict' ?
5. Explain arrow function and its benefits

## References :

- [Toptal Reference](https://www.toptal.com/javascript/interview-questions)
- [Interviewbit Reference](https://www.interviewbit.com/javascript-interview-questions/)
- [Hackr Reference](https://hackr.io/blog/javascript-interview-questions)
- [Sudher github interview preparation questions](https://github.com/sudheerj/javascript-interview-questions)
