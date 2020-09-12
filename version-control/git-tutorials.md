Git Commands :
Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows.

Frequently used gitcommands :

1.  git config
    Used to set basic configuration for the git

    > git config --global user.name "name"
    > git config --global user.email "mail-address"
    > git config --get user.name
    > git config --global --edit

        Edit value in git Editor

    > git config --global --add user.username MaheshGO

         Action
        --get                 get value: name [value-regex]
        --get-all             get all values: key [value-regex]
        --get-regexp          get values for regexp: name-regex [value-regex]
        --get-urlmatch        get value specific for the URL: section[.var] URL
        --replace-all         replace all matching variables: name value [value_regex]
        --add                 add a new variable: name value
        --unset               remove a variable: name [value-regex]
        --unset-all           remove all matches: name [value-regex]
        --rename-section      rename section: old-name new-name
        --remove-section      remove a section: name
        -l, --list            list all
        -e, --edit            open an editor
        --get-color           find the color configured: slot [default]
        --get-colorbool       find the color setting: slot [stdout-is-tty]

2.  git init <repo-name>
    Used to create new repository in Local
3.  git clone <git-url-shh-or-http>
    Used to clone existing Projct code into Local System
4.  git add <Files>
    Used to adds files into staging area.
    > git add . -> used to add all files in current directory to the staging area
    > git add \* -> used to add one or more to the staging area
    > git add info.txt
    >
    > > > Single command for git add All, commit and push , then use
    > > > git commit -am "your message" && git push
5.  git commit -m <message>
    Used to records or snapshots the file permanently in the version history
    > git commit -a
        This command commits any files you have added with the git add command and also commits any files you�ve changed since then.
6.  git diff
    Used to shows the file differences which are not yet staged.
    > > > To See Staged files commend use
    > > > git diff -staged
    > > > OR
    > > > git diff --cached
    > > > Too see the differences between the thwo branches use
    > > > git diff [first branch] [second branch]
7.  git reset
    Used to unstage the staged files
    > git reset <file>
        unstage only one file
    > git reset <commit>
        undoes all the commits after the specified commit and preserves the changes locally.
    > git reset --hard <commit>
        Discards all history and goes back to the specified commit
    > git reset --soft <commit>
        Commits after the specified commit, Changes will be in staging area.

Note : <Commit> means commit ID 8. git status
Used to displays paths that have differences between the index file and the current HEAD commit.
Options Mostly Used : > -s or --short -> Give the output in the short-format > -b or --branch -> Show the branch and tracking info even in short-format. > --show-stash -> Show the number of entries currently stashed away. > --long -> Give the output in the long-format. This is the default. > -v or --verbose -> In addition to the names of files that have been changed, also show the textual changes that are staged to be committed (i.e., like the output of git diff --cached). If -v is specified twice, then also show the changes in the working tree that have not yet been staged (i.e., like the output of git diff). 9. -u[<mode>] or --untracked-files[=<mode>] > Show untracked files.
Note : The mode parameter is used to specify the handling of untracked files. It is optional: it defaults to all, and if specified, it must be stuck to the option (e.g. -uno, but not -u no).
Modes :
1.no - Show no untracked files.
2.normal - Shows untracked files and directories.
3.all - Also shows individual files in untracked directories. 10. git rm - Command > git rm --cached <filename> - used to remove cached file name from git. > Used to deletes the file from your working directory and stages the deletion > git clean -df -> Remove all untracked directories and files. thats why it will be df. 11. git log
used to list the version history for the current branch >>> To see the version history of specific file the use > git log �follow <file> > git reflog -> show comitts in the order of last commits. 12. git show
Used to shows the metadata and content changes of the specified commit. > git show <commit> 13. git branch
Used to lists all the local branches in the current repository. >>> To create a new branch then use > git branch <branch-name> >>> To delete a existing branch, then use > git branch -d <branch-name> >>> To set default origin for git pull and push use, > git branch --set-upstream-to <remote>/<branch>  
 OR > git branch -u <remote>/<branch>  
14. git checkout
Used to switch from one branch to another > git checkout <branch-name> >>> To create new branch from current working directory and move to it then use > git checkout -b <new=branch-name> 15. git merge
Used to merges the specified branch�s history into the current branch > git merge <branch-name> 16. git remote
Used to connect your local repository to the remote server. > git remote add <variable-name> <Remote-Server-Link>
OR > git remote add origin <URL> >>> To List out all remote git repo's then use > git remote -v >>> To set one of remote to be an origin then use > git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
OR > git remote set-url origin <remote-name> 17. git push
Used to sends the committed changes into specified repository branch > git push <saved-remote-variable-name> <Branch-name> >>> To push current chnages to all the branches in specified repo use > git push --all <saved-remote-variable-name> >>> Delete Branch on remote repository - To delete a remote branch, we do not use the "git branch" command - but instead "git push" with the "--delete" flag: > git push origin --delete feature/login
OR > git push [variable name] :[branch name] 18. git pull
Used to fetches and merges changes on the remote server to your working directory.

19. git stash
    > git stash save - temporarily stores all the modified tracked files
    > git stash pop - restores the most recently stashed files
    > git stash list - lists all stashed changesets
    > git stash drop - discards the most recently stashed changeset

Not confirmed Commands : 20. git checkout <file>
if the file content is changed, then want to be revert with git index use above command 21. To Rename the commit message :
If the commit only exists in your local repository and has not been pushed to GitHub, you can amend the commit message with the git commit --amend command. > git commit --amend -m "New Commit Message"
It won't do any more commit it just modify last commit message. But i will change Last committed hash to new one. It because of commit message is also part of commit. When the hash changes it will change git history.
Note : If you changed git history, then it will affect other person git working tree. So Becareful here. > git commit --amend >>>It also used to commit file with out a new commit, file will be committed by its last commit.
If you have already pushed the commit to GitHub, you will have to force push a commit with an amended message. > git commit --amend -m "New Commit Message" > git push --force <branch>
Note : push --force command to force push over the old commit.
Note : If you need to amend the message for multiple commits or an older commit, you can use interactive rebase, then force push to change the commit history.

22. Recovering from a commit to wrong branch.
    git branch
    master
    ref-branch
    Accidentally commited to master.
    Goals :
    Master branch back it original (Before commit state).
    Commit should be in ref-branch
    Solution : git cherry-pick <commit>
    it will create new commit from it original commit Id. And it won't delete original commit from branch.
    Steps:
    Master : > git log -> get commit ID > git checkout ref-branch > git log - to verify commits > git cherry-pick <commit> > git checkout master > git reset --hard <commit> > git clean -df
    if you wants to last committed changes in master branch. That we are reset then use. > git reflog -> get commit ID that we want. > git checkout <copied-commit-id>

Problems : If we want to go back to old changes from new changes, But the new chnages already pulled by other peoples. Now we have to use git revert. It will create new commit on top those commit. the new commit completely undo all those chnages. > git revert <commit-hash> > git log -> check chnages.

Ref: [git quick ref](https://www.digitalocean.com/community/cheatsheets/how-to-use-git-a-reference-guide)
