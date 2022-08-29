> Conflict cannot survive without your participation. - Wayne Dyer

## When do merge conflicts occur?

A conflict arises when git is unable to automatically merge changes between two commits.

This happens when the same line of code is changed on multiple sources. Conflict often happens when multiple people work on the same branch, but it can also happen when working on the same lines of code in different branches.

Example:

Developer A and Developer B checkout code from the same remote repository and work on the same file. Developer A then pushes their code to the remote repository. Afterwards, developer B tries to push their changes to the same remote repository. However, he is unable to push the code and is greeted with the _Merge conflict_ message instead.

## How to recognize conflicted files?

When a conflict occurs, you will immediately notice conflict message in the terminal.

The conflicted file will also be marked red in the project view. When you open the file, you will notice additional lines in the file.

```
<<<<<<< HEAD
Content from e.g. main branch
=======
Content from some new branch
>>>>>>> branch_being_merged
```

The `=======` marks the center of the conflict, i.e. divides the content between the two conflicting sources.
Everything between `<<<<<<< HEAD` and `=======` is the content from the current branch which the HEAD reference points to.
Everything between `=======` and `>>>>>>> branch_being_merged` is the content in the branch you are trying to merge.

![git_conflicts_conflict.png](/img/git_conflicts_conflict.png)


## How to resolve conflicts?

There are a few ways to resolve conflicts. The easiest one is to open the conflicted file through a text editor or an IDE and make the necessary changes.

When resolving conflicted files, there are multiple approaches. Depending on how complicated the conflict is, you might prefer to use one over the other.


### Approach 1

The most straightforward approach.

1. Open the conflicted file and make the necessary changes

Nice and easy if there is a minor conflict. In case of multiple conflicted files or lines in a large file, it might get confusing.


### Approach 2

If you only want to keep the changes from one branch and don't care about the changes from the other one. You can simply accept all the changes from either branch.

1. Open the project view 
2. Right-click the conflicted file
3. Select _Git -> Resolve Conflicts..._
   - Conflicts window opens
   - Note the title and column names in the window, clearly stating what is being merged
4. Select _Accept Theirs_ to accept the changes from the merging branch
   - Alternatively, select _Accept Yours_ to accept the changes from the current branch (the branch you are merging into)

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
 <span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![git_conflicts_resolve_conflict_2.png](/img/git_conflicts_resolve_conflict_2.png)</span>
 <span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![git_conflicts_resolve_conflict_3.png](/img/git_conflicts_resolve_conflict_3.png)</span>
6. Click _Apply_ when you resolved all conflicts
   - Noted by _All conflicts resolved_ message in the upper-right corner

<span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![git_conflicts_resolve_conflict_4.png](/img/git_conflicts_resolve_conflict_4.png)</span>


## Saving changes

Once you resolved all the conflicts, you are still not done. First make sure everything is in order, then commit and push the changes.

1. Open the terminal
2. Run `git status`
   - You should see message saying all conflicts are fixed
3. Commit and push the changes

![git_conflicts_resolved.png](/img/git_conflicts_resolved.png)


### Resolving conflicts in a version control system

When using a VCS like GitHub or Bitbucket, you will see a warning after opening a pull request in case of a conflict. If that happens, fix the code on your machine and push the changes. Once you are done, if everything is ok, the warning should be gone.

1. Open the branch you were working on in PyCharm
2. Make the necessary changes to resolve the conflicts
3. Commit and push the changes
4. Verify that the conflict warning is no longer shown in the VCS


## Additional resources

[Resolving merge conflicts | GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)

[Resolve git conflicts | IntelliJ](https://www.jetbrains.com/help/idea/resolve-conflicts.html)

