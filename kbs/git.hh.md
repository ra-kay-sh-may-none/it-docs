#. Commits (unpushed):
  ##. Undo last commit but KEEP your changes (Staged):
    ###. git reset --soft HEAD~1
  ##. Undo last commit and UNSTAGE your changes:
    ###. git reset HEAD~1
  ##. Undo last commit and DELETE all changes (Destroy work):
    ###. git reset --hard HEAD~1
#. Commits (pushed):
  ##. Multistep below:
    ###.
      git revert HEAD
      git push origin <your-branch-name>
    ###.
