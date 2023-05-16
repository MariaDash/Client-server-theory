# Git_Additional_Repository 
### Additional git commands explanation
Notes:
* `git remote -v`  - Current remote repo,
* `git remote set-url origin https://github.com/MariaDash/XML_GIT.git`   - change remote repo to linked repo
* `git rm --cached filename` - make tracked file to be untracked
* `git ls-remote <remote>` full list of remote branches
* `git remote show <remote>`  - Full kist of remote branches and additional info.
## 1. Introduction
### 1.1. Create Github repo in browser version
### 1.2. Create folder 'Git' on PC. 
### 1.3. Go to that folder and clone repo there (using Git Bash):
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git
$ git clone https://github.com/MariaDash/Git_Additional.git
Cloning into 'Git_Additional'...
remote: Enumerating objects: 31, done.
remote: Counting objects: 100% (31/31), done.
remote: Compressing objects: 100% (21/21), done.
remote: Total 31 (delta 5), reused 10 (delta 0), pack-reused 0
Receiving objects: 100% (31/31), 7.08 KiB | 1.77 MiB/s, done.
Resolving deltas: 100% (5/5), done.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git
$

```
### 1.4. Checking what is located in this folder and status of repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git
$ ls
Git_Additional/

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git
$ cd Git_Additional/

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Repo is empty, so we can add files and track them with `git add`. On PC  in the folder we create file File1.txt. Look in the terminal for the result:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ touch File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        File1.txt

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.5.`git add`
In the File1.txt write `123` and make sure the system see this:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat >> File1.txt
123


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git add File1.txt
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Check status and see that new file now is tracking in the system and is saved in it.
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   File1.txt


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Change data in the file and again we check the status, see that there are two version of the file in the system: old one and new one:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ vim File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat File1.txt
123
321

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   File1.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   File1.txt


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
We can save new version or make restore to old, we save new :
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git add File1.txt
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Note: `git add .`  track all in the directory
### 1.6. `git commit`
Adding our first commit to the local repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git commit -m "test commit1"
[main 9740795] test commit1
 1 file changed, 2 insertions(+)
 create mode 100644 File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
After the commit we check status and see that there is nothing to commit but the file is still in the local repo.
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.7. `git push`
Now we can push it to remote repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 280 bytes | 140.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/MariaDash/Git_Additional.git
   140cd61..9740795  main -> main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.8. `git fetch`
To see if there are any differences between local and remore repo we choose command `git fetch`:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git fetch

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Here `main` is local branch and `origin/main` is a temporary branch that appear after executing `git fetch` command.
Do `git status` command: here we see that there is no difference between local and remote repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.9. `git pull`
Executing command `git pull` for updating information from remote to local repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 669 bytes | 74.00 KiB/s, done.
From https://github.com/MariaDash/Git_Additional
   589427a..60b5266  main       -> origin/main
Updating 589427a..60b5266
Fast-forward
 File1.txt | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
`589427a..60b5266` -unique hash of our commit.
Now we check and make sure that our branch has all updates:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Checking updated file:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat File1.txt
123
456
789.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
### 1.10. `git log`
Command `git log` can trace the commits:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git log
commit 60b526637f76a3626365ecffcfc60214c073c1e5 (HEAD -> main, origin/main, origin/HEAD)
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:55:59 2023 +0300

    Update File1.txt

commit 589427a7a438f8f050c1857e2505ffaaf57e79be
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:53:12 2023 +0300

    Update README.md

commit 9740795aaf7629aeca96cb053b083513512d64e2
Author: MariaDash <mafunta@gmail.com>
Date:   Sat May 6 13:43:04 2023 +0300

    test commit1

commit 140cd619a57e68e4adbecdb3d7365e2afe47e11f
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:31:38 2023 +0300


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
`q`- exit

Filter commits by author:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git log --author MariaDash
commit 60b526637f76a3626365ecffcfc60214c073c1e5 (HEAD -> main, origin/main, origin/HEAD)
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:55:59 2023 +0300

    Update File1.txt

commit 589427a7a438f8f050c1857e2505ffaaf57e79be
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:53:12 2023 +0300

    Update README.md

commit 9740795aaf7629aeca96cb053b083513512d64e2
Author: MariaDash <mafunta@gmail.com>
Date:   Sat May 6 13:43:04 2023 +0300

    test commit1

commit 140cd619a57e68e4adbecdb3d7365e2afe47e11f
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:31:38 2023 +0300


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.11. `git show`
Show changes in commit with defining the commit:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git show 589427a..60b5266
commit 60b526637f76a3626365ecffcfc60214c073c1e5 (HEAD -> main, origin/main, origin/HEAD)
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:55:59 2023 +0300

    Update File1.txt

diff --git a/File1.txt b/File1.txt
index 6841d18..2c73c19 100644
--- a/File1.txt
+++ b/File1.txt
@@ -1,2 +1,3 @@
 123
+456
+789.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Without defining hash of commit we will see the last commit:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git show
commit 60b526637f76a3626365ecffcfc60214c073c1e5 (HEAD -> main, origin/main, origin/HEAD)
Author: MariaDash <122399261+MariaDash@users.noreply.github.com>
Date:   Sat May 6 13:55:59 2023 +0300

    Update File1.txt

diff --git a/File1.txt b/File1.txt
index 6841d18..2c73c19 100644
--- a/File1.txt
+++ b/File1.txt
@@ -1,2 +1,3 @@
 123
+456
+789.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.12. `git blame`
To see who is author of the line of the commit:

1. 
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git blame File1.txt
9740795a (MariaDash 2023-05-06 13:43:04 +0300 1) 123
60b52663 (MariaDash 2023-05-06 13:55:59 +0300 2) 456
60b52663 (MariaDash 2023-05-06 13:55:59 +0300 3) 789.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
2. 
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git blame File1.txt| grep 123
9740795a (MariaDash 2023-05-06 13:43:04 +0300 1) 123

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
3 способ:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git blame File1.txt| grep MariaDash
9740795a (MariaDash 2023-05-06 13:43:04 +0300 1) 123
60b52663 (MariaDash 2023-05-06 13:55:59 +0300 2) 456
60b52663 (MariaDash 2023-05-06 13:55:59 +0300 3) 789.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
### 1.13. Adding strings into the file:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ echo "Add line" >> File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Check the changes (Also we cat use `cat`):
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   File1.txt

no changes added to commit (use "git add" and/or "git commit -a")

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.14. `git diff`
Show changes in another way:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git diff
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/File1.txt b/File1.txt
index 2c73c19..1f4f2eb 100644
--- a/File1.txt
+++ b/File1.txt
@@ -1,3 +1,4 @@
 123
 456
 789.
+Add line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Commiting all the files (that were earlier added):
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git commit -am "new commit"
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
[main 9ebf240] new commit
 1 file changed, 1 insertion(+)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 1.15. `git reset`
Reset the commit:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git reset HEAD~1
Unstaged changes after reset:
M       File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
## 2. Working with conflicts of files
### Notes:
 1) If we want to add our new file from local to remote repo, and on remote repo it is empty and at local it is changed, then we cannot use just `git push` . 
 It will be a conflict. First we must use `git pull` send different pieces of the file to local repo and after that `git push` our new file to the remote repo.
       
 Precondition: creating Conflict.txt on remote repo. 
 Creating newfile.txt, modifying File1.txt:
 ```
 Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ echo "new line" >> new.file

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ vim File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat File1.txt
123
commit test
456
789.
Add line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ 
```
Tracking and committing it all:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git add . && git commit -m "new changes"
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'new.file', LF will be replaced by CRLF the next time Git touches it
[main 09b7e6a] new changes
 2 files changed, 2 insertions(+)
 create mode 100644 new.file

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ 
```
 We cannot do  `git push`:
 ```
 Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
To https://github.com/MariaDash/Git_Additional.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/MariaDash/Git_Additional.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
First we must do git pull and write a commit:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git pull
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 691 bytes | 69.00 KiB/s, done.
From https://github.com/MariaDash/Git_Additional
   031b2cf..f375043  main       -> origin/main
Merge made by the 'ort' strategy.
 Conflict.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 Conflict.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
Enumerating objects: 10, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 643 bytes | 214.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/MariaDash/Git_Additional.git
   f375043..cecb408  main -> main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
 2) If we changed a file in the local repo and on the remote repo it is also changes but in another way then there is no option to `git push` from local to remote repo and we also cannot do `git pull`. So what we do: we open the file on the local PC and delete all the mess ( smth with `>>>>>` and `===`) and left only what we need), then do `git add`, `git commit` and `git push`. After that we can check that the files in both repos are equal.
 
 Precondition: changing in the File1.txt on remote repo first line to 'untesting line' . Changing in the File1.txt on local repo first line to 'testing line'.
Check the status:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   File1.txt

no changes added to commit (use "git add" and/or "git commit -a")

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git diff
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/File1.txt b/File1.txt
index 04854ca..2835228 100644
--- a/File1.txt
+++ b/File1.txt
@@ -1,4 +1,4 @@
-123
+testing line
 commit test
 456
 789.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Commit it:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git commit -am "test"
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
[main 51c195e] test
 1 file changed, 1 insertion(+), 1 deletion(-)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
And now we have errors both when we try to `git push` and `git pull`:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
To https://github.com/MariaDash/Git_Additional.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/MariaDash/Git_Additional.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 669 bytes | 47.00 KiB/s, done.
From https://github.com/MariaDash/Git_Additional
   cecb408..a74bae7  main       -> origin/main
Auto-merging File1.txt
CONFLICT (content): Merge conflict in File1.txt
Automatic merge failed; fix conflicts and then commit the result.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$

```
We check status:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   File1.txt

no changes added to commit (use "git add" and/or "git commit -a")

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$
```
See that both files are modified. We open a File1.txt ( where is a conflict) and look at the contents:
```
<<<<<<< HEAD
testing line
=======
untesting line
>>>>>>> a74bae7ca60cb2779b35b4283fef9cb507cd57b3
commit test
456
789.
Add line
```
We want to keep both different strings and we delete all the mess left( using vim):
```
testing line
untesting line
commit test
456
789.
Add line
```
We do git add, commit and push:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git add . && git commit -m "test"
[main 715ee30] test

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 574 bytes | 287.00 KiB/s, done.
Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/MariaDash/Git_Additional.git
   a74bae7..715ee30  main -> main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Now we can see that both files File1.txt in local and in remote repo are equal.

### 2.1. `git checkout`. Permanent rollback of changes:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ echo "3line" >> File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat File1.txt
testing line
untesting line
commit test
456
789.
Add line
3line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git checkout File1.txt
Updated 1 path from the index

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Checking rollback to previous commit:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat File1.txt
testing line
untesting line
commit test
456
789.
Add line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```

### 2.2. `git checkout .`. Permanent rollback of changes in two files at a time:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ echo "line" >> newfile.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat newfile.txt
line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ echo "line" >> Conflict.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat Conflict.txt
123
line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git checkout .
Updated 2 paths from the index

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$cat newfile.txt
new line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat Conflict
123

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
### 2.3. `git stash`, `git stash pop`. Temporary rollback of changes (pushing to temporary storage):
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ echo "test" >> Conflict.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat Conflict.txt
123
test

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git stash
warning: in the working copy of 'Conflict.txt', LF will be replaced by CRLF the next time Git touches it
Saved working directory and index state WIP on main: 715ee30 test

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat Conflict.txt
123

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Conflict.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (a9aa4479c43206a18f7254bf2e4f5cbf748e4649)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat Conflict.txt
123
test

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
### 2.4. `git stash clear`. Another way of permanent rollback of changes:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git stash clear

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git stash pop
No stash entries found.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ cat Conflict.txt
123
test

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Note: `git stash clear` delete all in stash storage.
## 3. Working with branches in Git:
### 3.1. `git branch`
Creating a new branch (branch is created on the last commit and copy it):
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch first_branch

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Checking that branch is created:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch
  first_branch
* main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
### 3.2. `git checkout branchname`
We are located on branch main. To switch to another branch we do:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git checkout first_branch
Switched to branch 'first_branch'
M       Conflict.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$

```
Checking for checkout:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git branch
* first_branch
  main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$
```
### 3.3. How to add changed file from new local branch to remote repo
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ echo "new branch line" >> File1.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ cat File1.txt
testing line
untesting line
commit test
456
789.
Add line
new branch line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git diff
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/Conflict.txt b/Conflict.txt
index 190a180..605d6eb 100644
--- a/Conflict.txt
+++ b/Conflict.txt
@@ -1 +1,2 @@
 123
+test
diff --git a/File1.txt b/File1.txt
index 247af2c..988ee46 100644
--- a/File1.txt
+++ b/File1.txt
@@ -4,3 +4,4 @@ commit test
 456
 789.
 Add line
+new branch line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git status
On branch first_branch
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Conflict.txt
        modified:   File1.txt

no changes added to commit (use "git add" and/or "git commit -a")

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git commit  -am "new branch commit"
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
[first_branch 828dbfd] new branch commit
 2 files changed, 2 insertions(+)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git push
fatal: The current branch first_branch has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin first_branch

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$

```
### 3.4. `git push -u origin first_branch`
Here we have an error while pushing a file, because on the remote repo there is no such branch as it is in local repo. We must link local branch to remote branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git push -u origin first_branch
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 414 bytes | 207.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'first_branch' on GitHub by visiting:
remote:      https://github.com/MariaDash/Git_Additional/pull/new/first_branch
remote:
To https://github.com/MariaDash/Git_Additional.git
 * [new branch]      first_branch -> first_branch
branch 'first_branch' set up to track 'origin/first_branch'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$

```
Checking:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ cat File1.txt
testing line
untesting line
commit test
456
789.
Add line
new branch line

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$
```
### 3.5. `git merge`
To switch to main branch and to merge all files we:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_branch)
$ git checkout -
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
Do merge of our local branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git merge first_branch
Updating 715ee30..828dbfd
Fast-forward
 Conflict.txt | 1 +
 File1.txt    | 1 +
 2 files changed, 2 insertions(+)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/MariaDash/Git_Additional.git
   715ee30..828dbfd  main -> main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
## 4. Working with branch conflicts
### 4.1. If on remote repo someone added a file, and on a local repo someone else added another file (two repo are not sincronized):
On the remote repo we have a file `Conflict branch` and on local repo we have changed `File1.txt`. we need to create another file second.file and push it to the remote repo.

Create new branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch second_branch

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch
  first_branch
* main
  second_branch

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Checkout to this new branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git checkout second_branch
Switched to branch 'second_branch'

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$
```
Creating a new file:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ echo "test_line" >> second.file

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ git status
On branch second_branch
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   File1.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        second.file

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ git add second.file
warning: in the working copy of 'second.file', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ git commit -am "add second.file"
[second_branch 6d0f6dd] add second.file
 1 file changed, 1 insertion(+)
 create mode 100644 second.file

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ git push -u origin second_branch
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 503 bytes | 251.00 KiB/s, done.
Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
remote:
remote: Create a pull request for 'second_branch' on GitHub by visiting:
remote:      https://github.com/MariaDash/Git_Additional/pull/new/second_branch
remote:
To https://github.com/MariaDash/Git_Additional.git
 * [new branch]      second_branch -> second_branch
branch 'second_branch' set up to track 'origin/second_branch'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
  
```
After that do merge:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git merge second_branch
Updating 828dbfd..3ca059c
Fast-forward
 newfile.txt | 2 +-
 second.file | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 newfile.txt
 create mode 100644 second.file

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
At this moment someone created a file "Conflict branch" on the branch "second_branch" on the  remote repo.
Do `git push`
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
To https://github.com/MariaDash/Git_Additional.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/MariaDash/Git_Additional.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
We have an error because on the remote repo we have another file changed.
So we do first `git pull` and then `git push`
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git pull
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 1.81 KiB | 53.00 KiB/s, done.
From https://github.com/MariaDash/Git_Additional
   828dbfd..4648813  main       -> origin/main
Updating 3ca059c..4648813
Fast-forward
 Conflict_branch | 1 +
 new.file        | 1 -
 2 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 Conflict_branch
 delete mode 100644 new.file

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
Everything up-to-date

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
### 4.2. Problem: when we need to change a string in a file both in remote and local repo:
On the remote repo we change file newfile.txt by adding string 'new file edit 2023'/ Jn the local repo we create new branch - swith to it and there we change newfile.txt by adding a string 'new file edit 2022':
Create a new branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch new_file_edit

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git checkout new_file_edit
Switched to branch 'new_file_edit'
M       File1.txt
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Here we change file at local repo.
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (new_file_edit)
$ git commit -am "edit 2021"
warning: in the working copy of 'File1.txt', LF will be replaced by CRLF the next time Git touches it
[new_file_edit ef05ef7] edit 2021
 2 files changed, 3 insertions(+), 2 deletions(-)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (new_file_edit)
$ git push  -u origin new_file_edit
Enumerating objects: 15, done.
Counting objects: 100% (14/14), done.
Delta compression using up to 4 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (10/10), 2.25 KiB | 164.00 KiB/s, done.
Total 10 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
remote:
remote: Create a pull request for 'new_file_edit' on GitHub by visiting:
remote:      https://github.com/MariaDash/Git_Additional/pull/new/new_file_edit
remote:
To https://github.com/MariaDash/Git_Additional.git
 * [new branch]      new_file_edit -> new_file_edit
branch 'new_file_edit' set up to track 'origin/new_file_edit'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (new_file_edit)
$

```
Checkout to main branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (new_file_edit)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git merge new_file_edit
Updating 4648813..ef05ef7
Fast-forward
 File1.txt   | 3 ++-
 newfile.txt | 2 +-
 2 files changed, 3 insertions(+), 2 deletions(-)

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
On a current moment someone changes this file on the remote repo.
Commands `git push` , `git pull` not working:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
To https://github.com/MariaDash/Git_Additional.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/MariaDash/Git_Additional.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 660 bytes | 44.00 KiB/s, done.
From https://github.com/MariaDash/Git_Additional
   4648813..b0e3cbe  main       -> origin/main
Auto-merging newfile.txt
CONFLICT (content): Merge conflict in newfile.txt
Automatic merge failed; fix conflicts and then commit the result.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$
```
We need  to change a file in the local repo (change lines in the file and then check it):
```
<<<<<<< HEAD
new file edit 2022
=======
new file edit 2023
>>>>>>> b0e3cbe7169f6714ebd7868b2764249cb2d8a191
```
we left only:
```
new file edit 2022
new file edit 2023
```
Then:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$ vim newfile.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$ cat newfile.txt
new file edit 2022
new file edit 2023


Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$

```
Track file:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$ git add newfile.txt

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$
```
Commit file:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main|MERGING)
$ git commit -am "changes are approved"
[main ed85868] changes are approved

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$
```
Push a file:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git push
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 316 bytes | 158.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/MariaDash/Git_Additional.git
   b0e3cbe..ed85868  main -> main

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
## 5.1. Renaming empty branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch first_name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch -m first_name second_name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ 
```
Checking:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git branch
  first_branch
* main
  new_file_edit
  second_branch
  second_name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$

```
## 5.2. Renaming not empty branch:
Creating new file in the new branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (main)
$ git checkout second_name
Switched to branch 'second_name'

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$ touch second.name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$ git add second.name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$ git commit -am "add second.name"
[second_name 6f744b7] add second.name
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 second.name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$

```
Push file on a branch:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$ git push -u origin  second_name
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 274 bytes | 274.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'second_name' on GitHub by visiting:
remote:      https://github.com/MariaDash/Git_Additional/pull/new/second_name
remote:
To https://github.com/MariaDash/Git_Additional.git
 * [new branch]      second_name -> second_name
branch 'second_name' set up to track 'origin/second_name'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$

```
Trying to rename:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_name)
$ git branch -m second_name first_name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$

```
On the local repo it is changed, on the remote repo it is not.
Deleting the branch on remote repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$ git push origin :second_name
To https://github.com/MariaDash/Git_Additional.git
 - [deleted]         second_name

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$
```
Push the file from local to origin with new branch_name:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$ git push -u origin  first_name
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 274 bytes | 274.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'first_name' on GitHub by visiting:
remote:      https://github.com/MariaDash/Git_Additional/pull/new/first_name
remote:
To https://github.com/MariaDash/Git_Additional.git
 * [new branch]      first_name -> first_name
branch 'first_name' set up to track 'origin/first_name'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$

```
## 5.3. Deleting branches from local repo:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$ git branch -d second_branch
Deleted branch second_branch (was 3ca059c).

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$
```
Restoring a branch from remote repo to local:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$ git fetch origin second_branch
From https://github.com/MariaDash/Git_Additional
 * branch            second_branch -> FETCH_HEAD

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$

```
Firstly the branch is not visible but when we checkout to it it we can see it:
```
Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$ git branch
  first_branch
* first_name
  main
  new_file_edit

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (first_name)
$ git checkout second_branch
Switched to a new branch 'second_branch'
branch 'second_branch' set up to track 'origin/second_branch'.

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$ git branch
  first_branch
  first_name
  main
  new_file_edit
* second_branch

Admin@DESKTOP-V6V9F0T MINGW64 /d/Testing_Course/New folder/Git/Git_Additional (second_branch)
$

```


##  git init


####  Create a local repository _GIT_init_.
To make a local repo, I just use `git init` command 
```
$ git init
Initialized empty Git repository in /d/Testing_Course/New folder/Git/.git
```
Now, we have add the file to make an initial (root) commit on _(master)_ branch:
```
$ git add .
```
Initial commit:
```
$ git commit -m "initial commit"
[master (root-commit) afcc9f0] initial commit
 1 file changed, 41 insertions(+)
 create mode 100644 Capitalcom_glossary_imgsrc.py
```
We have to create a `main` branch:
```
$ git branch -M main
```
And then we are automatically checked out at the `main` branch.
#### 2. Create a remote repository _First_ at GitHub.
To make this step, I go to my GitHub account, then go to the _"Repositories"_ tab and click on _"New"_ button.</br>
After this, I needed a link to this remote repo to connect it with my local repo in the very next step.
#### 3. Connect and synchronize these local and remote repositories.
To connect to the remote repo, I have a link to it. I can come back to terminal with a previously prepared initial commit.
```
$ git remote add origin https://github.com/MariaDash/First.git
```
The last thing is pushing that commit we created:
```
$ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 761 bytes | 761.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/MariaDash/First.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```
