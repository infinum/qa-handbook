> Conflict cannot survive without your participation. - Wayne Dyer

## When do merge conflicts occur?

A conflict arises when git is unable to automatically merge changes between two commits.

This happens when the same line of code is changed.
Conflict often happens when multiple people work on the same branch, but it can also happen when working in different branches.

Example:
Developer A and Developer B checkout code from the same remote repository and work on the same file.
Developer A then pushes their code to the remote repository. Afterwards, developer B tries to push their changes to the same remote repository. 
However, he is unable to push the code and is greeted with the _Merge conflict_ message instead.

## How to recognize conflicted files?

When a conflict occurs, you will immediately notice conflict message in the terminal.

The conflicted file will also be marked red in the project view.
When you open the file, you will notice additional lines in the file.

```
<<<<<<< HEAD
Content from e.g. main branch
=======
Content from some new branch
>>>>>>> branch_being_merged_from
```

Everything between `<<<<<<< HEAD` and `=======` is the content from the current branch which the HEAD ref points to.
Everything between `=======` and `>>>>>>> branch_being_merged_from` is the content in the branch you are trying to merge.

![git_conflicts_conflict.png](/img/git_conflicts_conflict.png)


## How to resolve conflicts?

There are a few ways to resolve conflicts. Probably the easiest one is to open the conflicted file through a text editor or an IDE and make the necessary changes.

When resolving conflicted files, there are multiple approaches. Depending on how complicated the conflict is, you can use one over the other.


### Approach 1

Open the conflicted file and make the necessary changes.


### Approach 2

1. Open the project view 
2. Right-click the conflicted file
3. Select _Git -> Resolve Conflicts..._
   - Conflicts window opens
4. Select _Accept Theirs_ to accept the changes from the merging branch
   - Alternatively, select _Accept Yours_ to accept the changes from the current branch

![git_conflicts_resolve_conflict_1.png](/img/git_conflicts_resolve_conflict_1.png)


### Approach 3

Use this approach if there are quite a few changes throughout the entire file, and you want to cherry-pick changes from both branches.

1. Open the project view 
2. Right-click the conflicted file
3. Select _Git -> Resolve Conflicts..._
   - Conflicts window opens
4. Double-click the conflicted file
   - A window showing the content in file from both branches opens
   - On the left-hand side is the file from the branch you are merging into
   - On the right-hand side is the file from the merging branch
5. Click the double-arrow (`>>` or `<<`)  next to the lines of code (from the left-hand or the right-hand side) that you want to keep
   - This will add the code to the _Result_ (content in the middle view) which is the content you wish to keep
   - Alternatively, click the `X` button next to the lines you **do not** want to keep
6. Click _Apply_ once you resolved all conflicts
   - Signaled by _All conflicts resolved_ in the upper-right corner

![git_conflicts_resolve_conflict_2.png](/img/git_conflicts_resolve_conflict_2.png)

![git_conflicts_resolve_conflict_3.png](/img/git_conflicts_resolve_conflict_3.png)

![git_conflicts_resolve_conflict_4.png](/img/git_conflicts_resolve_conflict_4.png)


## Check conflicts are resolved

1. Open the terminal
2. Run `git status`
   - You should see message saying all conflicts are fixed
3. Commit and push the changes

![git_conflicts_resolved.png](/img/git_conflicts_resolved.png)


### Resolving conflicts in VSC

If you are using a VCS like GitHub or Bitbucket, you will see a conflict warning after opening a pull request.

1. Open the branch you were working on in PyCharm
2. Make the necessary changes to resolve conflicts
3. Commit and push the changes
4. Verify that the conflict warning is no longer shown in the VSC


## Additional resources

[Resolving merge conflicts | GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)

[Resolve git conflicts | IntelliJ](https://www.jetbrains.com/help/idea/resolve-conflicts.html)

