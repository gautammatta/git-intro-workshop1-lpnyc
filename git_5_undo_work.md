# Undo work (Reset, Checkout, and Revert)

## Use cases

| Command        | Scope              | Common use cases |    
|----------------|--------------------|------------------|
| `git reset`    | Commit-level       | Discard commits in a private branch or throw away uncommited changes  |  
| `git reset`    | File-level	        | Unstage a file |
|                |                    |                |
| `git checkout` | Commit-level	      | Switch between branches or inspect old snapshots |
| `git checkout` | File-level	        | Discard changes in the working directory |
|                |                    |                |
| `git revert`	  | Commit-level	      | Undo commits in a public branch |
| `git revert`	  | File-level	        | (N/A) |


## Log of Commits
#### View log of Git
```bash
git log
```

#### View last 2 commits
```bash
git log -2
```  

>my example  

```
reshama$ git log -2
commit a3334f177bed83528f5ab3883d87f1336f599f49
Author: reshama <rs2715@gmail.com>
Date:   Tue May 24 11:04:52 2016 -0400

    adding test file 4

commit 12dc41f2620118977c17ad21dfc4b504191e170e
Author: reshama <rs2715@gmail.com>
Date:   Tue May 24 11:04:06 2016 -0400

    adding test3 file
reshama$ 
```  

## How to undo an add (undo a staged file)
```
git reset HEAD <file>       
```

## How to undo a commit
On the commit-level, resetting is a way to move the tip of a branch to a different commit. This can be used to remove commits from the current branch. For example, the following command moves the hotfix branch backwards by two commits.

```console
git reset --soft HEAD^     # use --soft if you want to keep your changes
git reset --hard HEAD^     # use --hard if you don't care about keeping the changes you made
```

```
git reset --soft HEAD~1    # use --soft to preserve changes that were made and undo last commit (~1 = back 1 commit)
```

#### Syntax for Windows Users
Note:  use `~` instead of `^`  

---

 
## Discard uncommitted changes to a file
Situation:  you've changed a file, but not yet committed the changes  
 
```bash
git checkout README
```

## Revert Commit
Reverting undoes a commit by creating a new commit. This is a safe way to undo changes, as it has no chance of re-writing the commit history. For example, the following command will figure out the changes contained in the 2nd to last commit, create a new commit undoing those changes, and tack the new commit onto the existing project.  
```bash
git checkout branch_name
git log -4
git revert HEAD~2
``` 
 
---

### References
[Reset, Checkout and Revert](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations)  
[Stack Overflow:  How do you undo the last commit](http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit)  
[Stack Overflow:  Remove files from last commit](http://stackoverflow.com/questions/12481639/remove-files-from-git-commit)  


