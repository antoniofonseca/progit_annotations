### First-Time Git Setup

```git
git config --list --show-origin
````

#### Your Identity
```git
git config --global user.name "John Doe""
git config --global user.email "johndoe@example.com""
```

#### Your Editor
```git
git config --global core.editor emacs
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
````

#### Your default branch name
```git
git config --global init.defaultBranch main
````

#### Checking Your Settings
```git
git config --list
git config user.name
git config --show-origin rerere.autoUpdate
````

#### Getting Help
```git
git help <verb>
git <verb> --help
man git-<verb>

git help config

git add -h
````

### Git Basics

#### Getting a Git Repository

for Linux:
```bash
cd /home/user/my_project
```

for macOS:
```bash
cd /Users/user/my_project
```

for Windows:
```bash
cd C:/Users/user/my_project
```

and type:
```bash
git init
````

```git
git add *.c
git add LICENSE
git commit -m 'Initial project version'
```

#### Cloning a exiting repository
```git
git clone https://github.com/libgit2/libgit2
````

### Recordind Changes to Repository

#### Checking the Status of Your Files

```git
git status
```

```git
echo 'My Project' > README
git status
````

#### Tracking New Files
```git
git add README
git status
````

#### Staging Modified Files
```git
git status
git add CONTRIBUTING.md
git status
````

```git
vim CONTRIBUTING.md
git status
```

#### Short Status
```git
git status -s
```

#### Ignoring Files
```git
cat .gitignore
````

#### Viewing Your Staged and Unstaged Changes

```git
git status
git diff
git diff --staged
git diff --cached
````

#### Commiting Your Chnages

```git
git commit
````

```git
git commit -m "Story 192: fix benchmarks for speed"
````

#### Skipping the Staging Area

```git
git status
git commit -a -m "Add new benchmarks"
````

#### Removing files

```bash
rm PROJECTS.md
git status
````

```git
git rm --cached README
```

```git
git rm log/\*.log
```

```git
git rm \*~
````

#### Moving Files

```git
git mv file_from file_to
````

```git
git mv README.md README
git status
````

### Viewing the Commit History

```git
git clone https://github.com/shacon/simplegit-progit
````

```git
git log
````

```git
git log -p -2
````

```git
git log --stat
````

```git
git log --pretty=oneline
````

```git
git log --pretty=format:"%h - %an, #ar : %s"
```

_Table 1. Useful specifiers for_ **git log --pretty=format**
| Specifier | Description of Output                           |
|-----------|-------------------------------------------------|
| %H        | Commit hash                                     |
| %h        | Abbreviated commit hash                         |
| %T        | Tree hash                                       |
| %t        | Abbreviated tree hash                           |
| %P        | Parent hashes                                   |
| %p        | Abbreviated parent hashes                       |
| %an       | Author name                                     |
| %ae       | Author email                                    |
| %ad       | Author date (format respects the --date=option) |
| %ar       | Author date, relative                           |
| %cn       | Committer name                                  |
| %ce       | Committer email                                 |
| %cd       | Committer date                                  |
| %cr       | Committer date, relative                        |
| %s        | Subject                                         |

```git
git log --pretty=format:"%h %s" --graph
````

_Table 2. Common options to_ **git log**
| Option          | Description                                                                                                                              |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| -p              | Show the patch introduced with each commit.                                                                                              |
| --stat          | Show statistics for files modified in each commit.                                                                                       |
| --shortstat     | Display only the changed/insertions/deletions line from the --stat command.                                                              |
| --name-only     | Show the list of files modified after the commit information.                                                                            |
| --name-status   | Show the list of files affected with added/modified/deleted information as well.                                                         |
| --abbrev-commit | Show only the first few characters of the SHA-1 checksum instead of all 40.                                                              |
| --relative-date | Display the date in a relative format (for example, “2 weeks ago”) instead of using the full date format.                                |
| --graph         | Display an ASCII graph of the branch and merge history beside the log output.                                                            |
| --pretty        | Show commits in an alternate format. Option values include oneline, short, full, fuller, and format (where you specify your own format). |
| --oneline       | Shorthand for --pretty=oneline --abbrev-commit used together.                                                                            |

#### Limiting Log Output

```git
git log --since=2.weeks
````

Helpful filter (_"pickaxe"_ option)
```git
git log -S function_name
````

Limiting to a file path
```git
git log -- path/to/file
````

_Table 3. Options to limit the output of_ **git log**
| Option            | Description                                                                  |
|-------------------|------------------------------------------------------------------------------|
| -\<n>              | Show only the last n commits                                                 |
| --since, --after  | Limit the commits to those made after the specified date.                    |
| --until, --before | Limit the commits to those made before the specified date.                   |
| --author          | Only show commits in which the author entry matches the specified string.    |
| --committer       | Only show commits in which the committer entry matches the specified string. |
| --grep            | Only show commits with a commit message containing the string                |
| -S                | Only show commits adding or removing code matching the string                |

```git
git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" --before="2008-11-01" --no-merges -- t/

#### Undoing Things

```git
git commit --amend
````

```git
git commit -m 'Initial commit'
git add forgotten_file
git commit --amend
````

#### Unstaging a Staged File

```git
git add *
git status
git reset HEAD CONTRIBUTING.md
git status
````

### Unmodifying a Modified File

```git
git checkout -- CONTRIBUTING.md
git status
```

### Undoing things with git restore

#### Unstaging a Staged File with git restore

```git
git add *
git status
git restore --staged CONTRIBUTING.md
git status
````

#### Unmodfifying a Modified File with git restore

```git
git retore CONTIBUTING.md
git status
```

### Working with Remotes

```git
git clone https://github.com/schacon/ticgit
cd ticgit
git remote
```

```git
cd gitgrit
git remote -v
```

#### Adding Remote Repositories

```git
git remote
git remote add pb https://github.com/paulboone/ticgit
git remote -v
````

```git
git fetch pb
```

#### Fetching and Pulling from Your Remotes

```git
git fetch <remote>
````

If you want the default behavior of git (fast-forward if possible, else create a merge commit): ```git config --global pull.rebase "false"```

If you want to rebase when pulling: ```git config --global pull.rebase "true"```

#### Pushing to Your Remotes

```git 
git push origin master
```

#### Inspecting a Remote

```git
git remote show origin
```

#### Renaming and Removing Remotes

```git
git remote rename pb paul
git remote
````

```git
git remote remove paul
git remote
```

### Tagging

#### Listing your Tags

```git
git tag
````

```git
git tag -l "v1.8.5*""
````

```git
git tag --list "v1.8.5*""
````

#### Creating Tags

#### Annotated Tags

```git
git tag -a v1.4 -m "my version 1.4"
git tag
````

```git
git show v1.4
````

#### Lightweight Tags

```git
git tag v1.4-lw
git tag
````

```git
git show v1.4-lw
````

#### Tagging Later

```git
git log --pretty=oneline
git tag -a v1.2 9fceb02
git tag
git show v1.2
````

#### Sharing Tags

```git
git push origin v1.5
```

```git
git push origin --tags
````

#### Pushing only annotated tags

```git
git push origin --follow-tags
```

#### Deleting Tags

```git
git tag -d v1.4-lw
```

#### deleting a tag from a remote server

```git
git push origin :refs/tags/v1.4-lw
```

```git
git push origin --delete <tagname>
```

#### Checking out Tags

```git
git checkout v2.0.0
```

```git
git checkout -b version2 v2.0.0
```

### Got Aliases

```git
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

```git
git config --global alias.unstage 'reset HEAD --'
````

```git
git unstage fileA
git reset HEAD -- fileA
````

```git
git config --global alias.last 'log -1 HEAD'
````

```git
git last
````

```git
git config --global alias.visual '!gitk'
````

#### Remove an Alias

```git
git config --global --unset alias.NAME
```


