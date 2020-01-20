```bash

student@M15013 MINGW64 ~/Desktop/TIL
$ ls
images/  markdown.md

student@M15013 MINGW64 ~/Desktop/TIL
$ pwd
/c/Users/student/Desktop/TIL

student@M15013 MINGW64 ~/Desktop/TIL
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/TIL/.git/

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git config --global user.name snowcuphea

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git congif --gobal user.email snowcuphea@gmail.com
git: 'congif' is not a git command. See 'git --help'.

The most similar command is
        config

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git config --global user.email snowcuphea@gmail.com

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git.md
        images/
        markdown.md

nothing added to commit but untracked files present (use "git add" to track)

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git add .
g
student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git.md
        new file:   images/catt.jpg
        new file:   images/image-20191205161852154.png
        new file:   markdown.md


student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'Init'
[master (root-commit) bda6d07] Init
 4 files changed, 144 insertions(+)
 create mode 100644 git.md
 create mode 100644 images/catt.jpg
 create mode 100644 images/image-20191205161852154.png
 create mode 100644 markdown.md

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git log
commit bda6d0785f0db062181ddbb14eb9db834216e922 (HEAD -> master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 16:52:23 2019 +0900

    Init

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ ^C

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ ^C

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   git.md

no changes added to commit (use "git add" and/or "git commit -a")

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git add .

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   git.md


student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'Git markdown 수정'
[master b94a6a9] Git markdown 수정
 1 file changed, 53 insertions(+), 1 deletion(-)

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git log
commit b94a6a92495913599e4f6100db80fb8ea822b4a6 (HEAD -> master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 17:07:18 2019 +0900

    Git markdown 수정

commit bda6d0785f0db062181ddbb14eb9db834216e922
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 16:52:23 2019 +0900

    Init

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git remote add origin https://github.com/snowcuphea/TIL.git

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git push -u origin master
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (10/10), 544.58 KiB | 20.94 MiB/s, done.
Total 10 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/snowcuphea/TIL.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git remote -v
origin  https://github.com/snowcuphea/TIL.git (fetch)
origin  https://github.com/snowcuphea/TIL.git (push)

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git push origin master
Everything up-to-date

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git add .

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'update
> '
[master 04816fd] update
 1 file changed, 35 insertions(+)

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'updateee'
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git log
commit 04816fdceb44fdd5f7665e628286117de6e6e9d0 (HEAD -> master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 17:30:16 2019 +0900

    update

commit b94a6a92495913599e4f6100db80fb8ea822b4a6 (origin/master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 17:07:18 2019 +0900

    Git markdown 수정

commit bda6d0785f0db062181ddbb14eb9db834216e922
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 16:52:23 2019 +0900

    Init

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'modified'
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
        modified:   git.md

no changes added to commit

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git add .

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   git.md


student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'hello'
[master cbf6f1c] hello
 1 file changed, 13 insertions(+), 1 deletion(-)

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git log
commit cbf6f1c4d7f54f29eac545761ec097dc9669d416 (HEAD -> master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 17:36:37 2019 +0900

    hello

commit 04816fdceb44fdd5f7665e628286117de6e6e9d0
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 17:30:16 2019 +0900

    update

commit b94a6a92495913599e4f6100db80fb8ea822b4a6 (origin/master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 17:07:18 2019 +0900

    Git markdown 수정

commit bda6d0785f0db062181ddbb14eb9db834216e922
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 16:52:23 2019 +0900

    Init

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git push origin master
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 1.20 KiB | 616.00 KiB/s, done.
Total 6 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/snowcuphea/TIL.git
   b94a6a9..cbf6f1c  master -> master

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'good'
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git push
Everything up-to-date

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git push origin master
Everything up-to-date

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git add .

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git commit -m 'nice'
[master 196e84e] nice
 1 file changed, 281 insertions(+)
 create mode 100644 "git\353\252\205\353\240\271\354\260\275.md"

student@M15013 MINGW64 ~/Desktop/TIL (master)
$ git push origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1.79 KiB | 1.79 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/snowcuphea/TIL.git
   cbf6f1c..196e84e  master -> master

student@M15013 MINGW64 ~/Desktop/TIL (master)
$


```

