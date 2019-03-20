# `git` Cheatsheet

![Lynda logo](http://cdn.lynda.com/assets/1730-r20151015/Website/ui/images/mediakit/logos-gif/lynda_logo1k-d_72x72.gif)

The following are notes from Kevin Skoglund's [Git Essential Training](http://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html) in the [Lynda.com library](http://www.lynda.com). For a full explanation of the commands and their usage, check out that course.

__Table of Contents:__

1. [`git` Help](#git-help)
2. [`git` Setup](#git-setup)
3. [`git` Configuration](#git-configuration)
4. [`git` Auto-completion (Mac)](#git-auto-completion-mac)
5. [Common `git` Aliases](#common-git-aliases)
6. [Common `git` Commands](#common-git-commands)
7. [Simple `git` Workflow](#simple-git-workflow)
8. [`git` Tree-ish](#git-tree-ish)
9. [`git` Logs](#git-logs)
10. [`git` Compare Differences](#git-compare-differences)
11. [`git` Stash](#git-stash)
12. [`git` Branches](#git-branches)
13. [`git` Merges](#git-merges)
14. [`git` Deletion & Changes](#git-deletion-and-changes)
15. [`git` Remotes](#git-remotes)
16. [Collaboration Workflow Example](#collaboration-workflow-example)

### `git` Help
```bash
which git                                               = Do I have git? What’s its path?
git -- version                                          = Which version of git?
git help                                                = List of possible commands
git help <command>                                      = Help for that command
git <command> --help                                    = Same as above
```

[Back to top](#git-cheatsheet)

### `git` Setup
```bash
git init                                                = Initialize git here
git clone <url>                                         = Clone a remote repo here
git clone <url> <folder_name>                           = Clone remote project in folder
git clone -b <branch> <url>                             = Clone a different branch
```

[Back to top](#git-cheatsheet)

### `git` Configuration
```bash
git config                                              = Git config for Project
git config --global                                     = Git config for User
git config --system                                     = Git config for System
git config --global user.name “Your Name”               = Set your name
git config --global user.email “u@mail.com”             = Set your email
git config --global core.editor “editor”                = Default code editor
git config --global core.excludesfile ~/.gitignore      = Global
git config --global color.ui true
git config --list                                       = Show what’s in .gitconfig
cat ~/.gitconfig                                        = Show what’s in User .gitconfig
```

[Back to top](#git-cheatsheet)

### `git` Auto-completion (Mac)
```bash
cd ~                                                    = Change to User directory

curl -OL https://github.com/git/git/raw/master/contrib/completion/git-completion.bash = Download

mv ~/git-completion.bash ~/.git-completion.bash         = Rename and make a hidden file
nano .bash_profile                                      = Create/edit .bash_profile

if [ -f ~/.git-completion.bash ]; then                  = Save this in .bash_profile
  source ~/.git-completion.bash 
fi 

export PS1=‘\W $(__git_ps1 “(%s)”)$ ’                   = Save in .bash_profile to permanently show current branch in Prompt String
echo $PS1                                               = Shows current Prompt String
__git_ps1                                               = Shows current branch
```

[Back to top](#git-cheatsheet)

### Common `git` Aliases
```bash
git config --global alias.st “status”
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.df diff
git config --global alias.dfs “diff --staged”
git config --global alias.logg “log --graph --decorate
--oneline --abbrev-commit --all --colored”
```

[Back to top](#git-cheatsheet)

### Common `git` Commands
```bash
~/                                                      = User directory
pwd                                                     = Check Present Working Directory path
cd <path>                                               = Change directory to <path>
cat <file>                                              = View the contents of a file
ls -la                                                  = Show all contents of a directory
nano <file>                                             = Use the nano text editor in Terminal
touch <file>                                            = Create an empty file
touch <empty_dir>/.gitkeep                              = Track empty dir
git status                                              = What’s going on with git?
```

[Back to top](#git-cheatsheet)

### Simple `git` Workflow
```bash
git status                                              = What’s going on with git?
git add <file>                                          = Add this file to Staging Index
git add .                                               = Add ALL files to Staging Index
git commit -m “Message”                                 = Commit changes
git commit -am “Message”                                = Non-Staging commit
git diff                                                = Compare file changes in pwd
git diff --staged                                       = Compare changes in Staging
git log                                                 = Show previous commits
```

[Back to top](#git-cheatsheet)

### `git` Tree-ish
```bash
master | HEAD | <SHA#> | HEAD^ | HEAD^^ | HEAD~3        = <tree-ish>
git ls-tree <tree-ish>                                  = List your trees
```

[Back to top](#git-cheatsheet)

### `git` Logs
```bash
git log --oneline -3                                    = Show condensed git log (with 7-digit SHA#) for only the previous 3 commits
git log --since=“2014-08-31”                            = Show commits since (also after) that date
git log --until=“2014-09-15”                            = Show commits until (also before) that date
git log --since=“2 weeks ago” --until=“3 days ago”      = Show commits between those times
git log --since=2.weeks --until=3.days                  = Same as above
git log --author=“Name”                                 = Show commits by that author
git log --grep=“string”                                 = Search all commits for given “string”
git log <SHA#>..<SHA#>                                  = Show commits between 2 SHA#s (or other <tree-ish>)
git log <SHA#>.. <file>                                 = Show commits from that SHA# to only that file
git log -p <SHA#>.. <file>                              = Show the exact changes (the “patch”) to the files between commits
git log --stat --summary --graph                        = Statistics, summary & graph (all branches & merges) of the changes
git log --oneline --graph --all --decorate              = Show a condensed, colored, graph of ALL the commits
git log --format=oneline | =short | =medium | =full | =fuller | =email | =raw         = Log formatting
```

[Back to top](#git-cheatsheet)

### `git` Compare Differences
```bash
git diff <SHA#>                                         = Compare difference between HEAD and SHA#
git diff <SHA#> <file>                                  = Compare difference between HEAD and SHA# of a particular file
git diff <SHA#>..<SHA#>                                 = Compare difference between two SHA#s
git diff --stat --summary <tree-ish>..<tree-ish> <file> = Show summary and stats of a file between two tree-ish
git diff --ignore-space-change <tree-ish>..<tree-ish>   = git diff -b <tree-ish>..<tree-ish>
git diff --ignore-all-space <tree-ish>..<tree-ish>      = git diff -w <tree-ish>..<tree-ish>
git diff master..<new_branch>                           = Compare two branches
git diff --color-words master..<new_branch>             = Comparisons are shown on the same line in red and green
git show <SHA#>                                         = Show more info about the commit + diff between commits
git show --format=oneline HEAD                          = Show condensed diff info about the latest commit
```

[Back to top](#git-cheatsheet)

### `git` Stash
```bash
git stash save “Message”                                = Put something in the Stash
git stash list                                          = Returns stash@{#}: On <branch>: “Message” = Shows what you’ve got where
git stash show stash@{#}                                = Show the diff stat about what changed in that file
git stash show -p stash@{#}                             = Show EXACT changes you made (a “patch”)
git stash pop stash@{#}                                 = Remove this from the Stash and put it in the Working Directory
git stash apply                                         = Copy this from the Stash and put it in the Working Directory
git stash drop stash@{#}                                = Delete from the Stash
git stash clear                                         = Delete EVERYTHING from the Stash
```

[Back to top](#git-cheatsheet)

### `git` Branches
```bash
git branch                                              = Show branches in Working Directory (show * next to current branch)
git branch <new_branch>                                 = Make a new branch
git checkout <branch>                                   = Switches to that branch
git checkout -b <new_branch>                            = Make a new branch AND switch to it
git branch --merged                                     = Show all branches that are merged with current branch
git branch --no-merge                                   = Show which branches are NOT merged
git branch -m <branch> <new_name>                       = git branch --move <branch> <new_name> = Move or Rename a branch
git branch -d <branch> = git branch --delete <branch>   = Delete a branch
git branch -D <branch>                                  = Force delete a branch
git branch -r                                           = Show only remote branches
git branch -a                                           = Show ALL branches
```

[Back to top](#git-cheatsheet)

### `git` Merges
```bash
git diff <branch> <branch>                              = Compare two branches
git checkout master                                     = Switch to branch to RECEIVE changes
git merge <branch>                                      = Merge <branch> into current branch
git merge --no-ff <branch>                              = Force merge (non-fast-forward)
git merge --only-ff <branch>                            = Only merge if fast-forward
git merge --abort                                       = Abort a merge if there are conflicts
git mergetool tool=tool_name                            = Call a merge tool
```

[Back to top](#git-cheatsheet)

### `git` Deletion and Changes
```bash
git mv <old-name> <new-name>                            = Move/Rename
git rm <file>                                           = Delete that file
git rm --cached <file>                                  = Stop tracking that file
git checkout -- <file>                                  = Pull file to Staging Index
git reset HEAD <file>                                   = Undo changes in Staging Index
git commit --amend -m “Message”                         = Rewrite commit
git revert <SHA#>                                       = Undo A to B changes
git reset <SHA#>                                        = Move HEAD pointer here
git reset --soft <SHA#>                                 = Don’t change SI nor PWD
git reset --mixed <SHA#>                                = Change SI, not PWD
git reset --hard <SHA#>                                 = Make SI & PWD match repo
git clean                                               = Remove untracked files in Working Directory
git clean -n                                            = Test run (“Would remove...”)
git clean -f                                            = Remove untracked files from PWD, not SI
```

[Back to top](#git-cheatsheet)

### `git` Remotes
```bash
origin/master                                           = The remote repo on your local machine
git diff origin/master..master                          = Check remote and local
git branch -r                                           = Show any new branches on the remote
git merge origin/master                                 = Merge with local copy of origin
git remote                                              = Shows list of remote repos git knows about
git remote add origin <url>                             = Add a remote named “origin” with the GitHub URL
git remote -v                                           = “View” the name and URL of the default repo you will push and fetch from
git remote rm <alias>                                   = Remove that repo
git push -u <alias> <branch>                            = Push the <branch> to your <alias> repo. -u sets it as your default
git push origin master                                  = Push local repo to the remote repo git push = Push the default tracking branch
git fetch <alias>                                       = Go to the remote repo and retrieve it git fetch = Get the default origin repo
git pull                                                = git fetch + git merge
git branch <non_tracking> origin/<non_tracking>         = Create new branch from a non-tracking repo branch and track it
git checkout -b <non_tracking> origin/<non_tracking>    = Same as above
git config branch.<branch>.remote origin branch.<branch>.merge refs/heads/master = Start tracking remote br
git branch --set-upstream <branch> origin/<branch>      = Start tracking a remote branch
git push origin --delete <non_tracking>                 = Delete a non-tracking branch from the remote
```

[Back to top](#git-cheatsheet)

# Collaboration Workflow Example

##### You
```bash
1. Set up the remote repo + push the master branch
2. git checkout master                                  = Switch to master
3. git fetch                                            = Check if there are changes to the remote
4. git merge origin/master                              = Merge changes with your local repo
5. git checkout -b <new_feature>                        = Create a new branch to work on a new feature
6. git add <file(s)>                                    = Add new files to Staging Index
7. git commit -m "Message"                              = Commit the new files and/or changes
8. git fetch                                            = See if there’s anything new on the remote (again)
9. git push -u origin <new_feature>                     = Push the new branch to the remote so your colleagues can view/fetch it
10. Email colleague about the changes
```

##### Colleague
```bash
1. git clone <url>                                      = Create the repo on her desktop if not already present
2. git checkout master                                  = Switch to master
3. git fetch                                            = Check if there are changes to the remote
4. git merge origin/master                              = Bring everything up to date
5. git branch -r                                        = Check if there are new branches on the remote
6. git checkout -b <new_feature> origin/<new_feature>   = Create and track the new feature branch on the remote
7. git log                                              = Show what’s happened in the last few commits
8. git show <SHA#>                                      = Show the specific commit made to the new feature
9. Edit the new feature
10. git commit -am “Message”                            = Add + commit changes
11. git fetch                                           = Anything new on the remote?
12. git push                                            = Push it back up to the remote
13. Email reply
```

##### You
```bash
1. git fetch                                            = Anything new?
2. git log -p <new_feature>..origin/<new_feature>       = Show the “patch” (exact changes) to the new feature branch
3. git merge origin/<new_feature>
4. Edit the new feature
5. git checkout master                                  = Switch to master
6. git fetch                                            = Anything new?
7. git merge origin/master                              = Merge with your local origin
8. git merge <new_feature>                              = Merge the new feature into master
9. git push                                             = Get everything up on the remote
```

[Back to top](#git-cheatsheet)
