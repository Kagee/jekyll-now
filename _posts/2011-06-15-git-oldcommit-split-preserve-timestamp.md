---
layout: post
status: publish
published: true
title: 'Git: Splitting a old git commit while preserving commit timestamps'
date: !binary |-
  MjAxMS0wNi0xNSAwNzozMDo0NSArMDIwMA==
date_gmt: !binary |-
  MjAxMS0wNi0xNSAwNTozMDo0NSArMDIwMA==
categories:
- git
---
While cleaning (svn to git) the sourcecode from my bachelor thesis, i now and then needed to split a commit into two. When doing this, i still wanted to preserve the original timestamp. 
<!-- more -->
```bash
user@host ~/tmp $ git init .
Initialized empty Git repository in /home/user/tmp/.git/
user@host ~/tmp (master) $ echo -e "Hello World.\nHow are you?" > fileA.txt
user@host ~/tmp (master*) $ ls
fileA.txt  fileB.txt  fileC.txt  fileD.txt
user@host ~/tmp (master*) $ git add fileA.txt
user@host ~/tmp (master*) $ git commit -m'Added file A'
[master (root-commit) ada1ac0] Added file A
 1 file changed, 2 insertions(+)
 create mode 100644 fileA.txt
user@host ~/tmp (master*) $ echo -e "I am fine, you?\nAll well, thank you." > fileB.txt
user@host ~/tmp (master*) $ echo -e "When are we meeting for dinner?\nAt 18:00, don't you dare forget\!" > fileC.txt
user@host ~/tmp (master*) $ git add fileB.txt fileC.txt 
user@host ~/tmp (master*) $ git commit -m'Added file B'
[master 50b737a] Added file B
 2 files changed, 4 insertions(+)
 create mode 100644 fileB.txt
 create mode 100644 fileC.txt
user@host ~/tmp (master*) $ echo -e "Bugger, we added two files in the last committ \!\nDon't worry, I know what to do\!" > fileD.txt
user@host ~/tmp (master*) $ git add fileD.txt 
user@host ~/tmp (master*) $ git commit -m'Added file D'
[master 2563a97] Added file D
 1 file changed, 2 insertions(+)
 create mode 100644 fileD.txt
user@host ~/tmp (master) $ git log --format=oneline | cat
2563a976d8d87e8c30466549eccd1dc8e690fe4e Added file D
50b737ae21790ec309f61024257c7f5d27e12365 Added file B
ada1ac0a2b823e93e2ede64b17b803d9628414a7 Added file A
```
Daam, commit ```50b737a``` was supposed to be two commits!
...
```bash
hildenae@ick:~/tmp/wwsvntogit/WizardWars$ git rebase -i c2180
Stopped at be7755e... Comments
You can amend the commit now, with
	git commit --amend
Once you are satisfied with your changes, run
	git rebase --continue
hildenae@ick:~/tmp/wwsvntogit/WizardWars$ git reset HEAD^
Unstaged changes after reset:
M	parser/createSG/src/no/hig/rag/parser/BuildInitialSceneGraph.java
M	parser/createSG/src/no/hig/rag/parser/ColladaParse.java
M	parser/createSG/src/no/hig/rag/parser/GameObject.java
M	parser/createSG/src/no/hig/rag/parser/Main.java
M	parser/createSG/src/no/hig/rag/parser/MtlParse.java
M	parser/createSG/src/no/hig/rag/parser/ObjParse.java
hildenae@ick:~/tmp/wwsvntogit/WizardWars$ git commit -c be7755e -- parser/createSG/src/no/hig/rag/parser/MtlParse.java parser/createSG/src/no/hig/rag/parser/ObjParse.java
[detached HEAD 7b4ef13] Remove unused classes from createSG
 2 files changed, 0 insertions(+), 382 deletions(-)
 delete mode 100644 parser/createSG/src/no/hig/rag/parser/MtlParse.java
 delete mode 100644 parser/createSG/src/no/hig/rag/parser/ObjParse.java
hildenae@ick:~/tmp/wwsvntogit/WizardWars$ git commit -ac be7755e
[detached HEAD 1a6d313] Add javadoc comments and cleanup sourcecode
 4 files changed, 37 insertions(+), 48 deletions(-)
hildenae@ick:~/tmp/wwsvntogit/WizardWars$ git rebase --continue
Successfully rebased and updated refs/heads/master.
```</p>
<h3>Referenses</h3>
<ul>
<li>http://book.git-scm.com/4_interactive_rebasing.html</li>
<li>http://manpages.ubuntu.com/manpages/maverick/man1/git-commit.1.html#contenttoc3</li>
</ul>
