# What are <img width="86" height="36" alt="git" src="https://git-scm.org/images/logo@2x.png"> & GitHub <img width="80" alt="GitHub Octocat" src="https://github.githubassets.com/images/modules/logos_page/Octocat.png"> ?

IMPORTANT PRINCIPLE:  AVOID E-MAILING "SOURCE CODE" =  "INSTRUCTIONS OF A COMPUTER PROGRAM IN TEXT" ("RECIPE FOR CONFUSION BY VERSIONITIS.")

INSTEAD: Store the files related to a project in a remote repository ("repo") and e-mail your collaborators that the latest versions of
the files are available "on GitHub" or any other remote repository hosting platform like GitLab, BitBucket, or a private git server on
your "intranet."

# The "Big Picture"

```
# Use git status periodically to have git provide you with its view of the repo(s)

                                                                           GitHub
                                                                           -----------
                                                                           hello.py[0]


working dir           staging area              local repo                 GitHub
-----------           ------------              ----------    git clone    -----------
hello.py[0]                                     hello.py[0]      <---      hello.py[0]


[edit the file]
working dir           staging area              local repo                 GitHub
-----------           ------------              ----------                 -----------
hello.py[1]                                     hello.py[0]                hello.py[0]


working dir           staging area              local repo                 GitHub
-----------  git add  ------------              ----------                 -----------
hello.py[1]    --->   hello.py[1]               hello.py[0]                hello.py[0]
...                   ...
                     

working dir           staging area              local repo                 GitHub
-----------           ------------  git commit  ----------                 -----------
hello.py[1]                           --->      hello.py[1]                hello.py[0]
...                                             ...


working dir           staging area              local repo                 GitHub
-----------           ------------              ----------    git push     -----------
hello.py[1]                                     hello.py[1]     --->       hello.py[1]
...                                             ...                        ...
```


# <img width="55" height="23" alt="Git" src="https://git-scm.org/images/logo@2x.png"> :
* a software environment running on a single (stand-alone) computer
* helps users track versions (including branches) of files related to a project
* based on the concept of a repository, a.k.a. (also known as) "repo," which is like a folder
* can connect to remote repos....



<img width="80" alt="GitHub Octocat" src="https://github.githubassets.com/images/modules/logos_page/Octocat.png"> GitHub is a site on the
Internet that allows `git` users to host remote versions of their repos.
* Other similar sites: GitLab, BitBucket, etc. ~ GitHub is _*NOT*_ the only possibility (In 2018 Microsoft acquired GitHub)
* "Private Server" ~ https://github.com/enterprise

FOR EXAMPLE:  In class, you could clone a remote GitHub repo to your computer in the lab.  Before you left class, you should push your
files up to your remote repo (on GitHub).  In the Library, you could clone your GitHub repo to a computer in the InfoCommons and do some work.
As long as you pushed your files on the InfoCommons computer to your remote GitHub repo, you could then go home and clone the files down to a
computer at home to do more work.

NOTE:  Many class sessions & homework assignments will be GitHub remote repos.

`git` on Windows: <img src='https://avatars0.githubusercontent.com/u/4571183?s=200&v=4' width=50 height=50>

NOTE: Logos of git show branches, because branches are fundamental to `git`.

## Basic `git` commands

Here is the first set of `git` commands that we will use:

|command|Effect
|:------|:----------|
|`git --version` | What version of git?   Also can be a test to see if `git` is accessible (`git` provides lengthy output) |
|`git status`    | Status of files in a repository (must be in a `git` repo for this command to be meaningful|
|`git clone <URL> [local]` | Find the remote repo at `URL` and copy it into a folder with the same name, or (optional) with the (different) name: `local`|
|`git add local`| `git clone URL` above assumes a pre-existing remote repo -- to get started "from scratch," use this command to start a local repo|
|`git add <file(s)>`| Add the named file(s) to the "staging area" ~ to be committed together in one batch |
|`git commit -m 'description'`| Commit the files in the staging area as a batch to (local) "repo" (repository)  |
|`git push`      | Push the changes from the local repository to the remote repository that was previously `git clone`d |


## Let's `git` Started!

Find where `git` is on your computer.  Type `git --version` into either
* Linux & MacOS:
  Console or terminal window
* Windows
  * Anaconda PowerShell Prompt (Anaconda Prompt is being depreated or retired) or `git bash`
  * You may need to push "Windows+S" to search for "Anacoda" or "Git Bash."

Try Anaconda PowerShell Prompt first, and if that is not connected to `git`, then use `git bash` (avoid Anaconda Prompt if possible).

### "Sidebar" on operating systems
* The "internals" of an operating system is commonly called "the kernel," as in the hidden or interior of a nut,
  * scheduler
  * memory manager
  * file system
  * drivers ~ software to I/O (input/output) devices like the display, USB (universal serial bus), network interface card (NIC), ...
* The "exterior" of an operating system is commonly called "the shell," as in the outer or visible part of a nut.

A graphical user interface (GUI) is  actually the shell of an operating system.

The console or terimal is a.k.a. a command line interface (CLI), and is also a kind of shell for the operating system.

Different operating systems could have the same shell.  For example, older Macs ran on the PowerPC central processing unit (CPU),
but when MacOS moved to the Intel architecture of CPU, the kernel changed, but the shell (MacOS GUI) did not.
```
> git status

fatal: not a git repository (or any of the parent directories): .git
```

## `clone` this remote repository on GitHub to your local computer
PICTURE 0
```
                                                 local repo                 GitHub
                                                 ----------                -----------
                                                                           hello.py[0]
```


`cd` into what will become the parent directory for the `git` repo (short for "repository").

EXAMPLE:
```
cd ~/          # usually returns to your home directory
cd Documents   # Next, you will clone the remote repo underneath ~/Documents
```

Notice the green "Clone or download" button button in the upper right of the Web view of the remote repo.

Click it to pull-down the options, including the URL which will be something like:
```
      https://github.com/ics111-204/c00-<yourhandle>.git
                         ^^^^^^^^^^ ||||||||||||||||
                        organization   remote repo
```

Type either one of the following (but __*NOT*__ both):
```
     git clone https://github.com/ics211-200/c03-abc123.git
     git clone https://github.com/ics211-200/c03-abc123.git c03
```

The first will create a local repo with the same name as the remote repo: `c03-abc123` while the
second will have the local name `c03` instead of the long default name.

PICTURE 1a
```
                                                 local repo                 GitHub
                                                 ----------    git clone    -----------
                                                 hello.py[0]     <----      hello.py[0]
```


## `cd` into the new local repo & update `hello.py`

`cd c03` (or `cd c03-abc123`)

```
> git status

On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

PICTURE 1b
```
working tree                                     local repo                 GitHub
------------                                     ----------    git clone    -----------
hello.py[0]                                      hello.py[0]     <----      hello.py[0]
```
Picture 1b is actually a truer version of what happened.  Above (1a), you didn't yet 
realize that the working tree that you see is itself a local clone of the repo.

What is origin?
```
> git remote

origin

> git remote -v   # verbose

origin   https://github.com/ics211-200/c03-abc123.git (fetch)
origin   https://github.com/ics211-200/c03-abc123.git (push)
```

## Edit `hello.py` as directed by its DOCSTRING.

After the edits, check `git status`

```
> git status

On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
         modified:   hello.py
 
 no changes added to commit (use "git add" and/or "git commit -a")
 ```
 
 PICTURE 2
 ```
 working dir           staging area              local repo                 GitHub
 -----------           ------------              ----------                 -----------
 hello.py[1]                                     hello.py[0]                hello.py[0]
 ```

## Stage the updated file: `git add <filename>`

```
> git add hello.py

> git status

On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   hello.py

```

## PICTURE 3
```
working dir           staging area              local repo                 GitHub
-----------  git add  ------------              ----------                 -----------
hello.py[1]   --->    hello.py[1]               hello.py[0]                hello.py[0]
```

## Store the updated file into the local repo using `git commit -m 'message'`

```
> git commit -m 'updated'

[master 80db47] updated
 1 file changed, 21 insertions(+)
 create mode 10064 hello.py

> git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

## Archive the updated file to the remote repo using `git push`
```
> git push

Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 579 bytes | 579.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/ics211-200/c03-abc123
   5c8fdf9..80dbd47  master -> master
```
