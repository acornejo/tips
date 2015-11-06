# git-advanced

To squash the last N commits together:

    git reset --soft HEAD~N
    git commit -m "new commit message"

If you want to squash the last N commits and edit a commit message which
includes all previous commit messages:

    git reset --soft HEAD~N
    git commit --edit -m"$(git log --format=%B --reverse HEAD..HEAD@{1})"

To delete a branch branchname, both locally and in the remote origin:

git branch -d branchname git push origin :branchname

Given a branch branchname and a remote upstream, if you want your local
branch to be a mirror of the remote branch, do the following:

git checkout branchname git fetch upstream git reset --hard
upstream/branchname git clean -dfx
