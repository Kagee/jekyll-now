---
layout: post
status: publish
published: true
title: Trekke ut deler av et git-repository, og samtidig ta vare på historie
updated: 2014-10-10 15:38:00 +0200
date: 2011-04-15 19:45:12 +0200
categories:
- bash
- norwegian
---
Trekke ut deler av et git-repository, og samtidig ta vare på historie
<!--more-->
<p><strong>Clone</strong>
{% highlight bash %}
git clone git@github.com:Kagee/fixmystreet.git
Initialized empty Git repository in /home/hildenae/tmp/fixmystreet/.git/
remote: Counting objects: 10461, done.
remote: Compressing objects: 100% (3306/3306), done.
remote: Total 10461 (delta 6802), reused 10276 (delta 6713)
Receiving objects: 100% (10461/10461), 10.10 MiB | 497 KiB/s, done.
Resolving deltas: 100% (6802/6802), done.</p>
<p>cd fixmystreet/</p>
<p>ls
android  bin  commonlib  conf  db  iphone  LICENSE.txt  locale  notes  perllib  README.pod  t  templates  web  web-admin</p>
<p>ls android
Fix My Street  README.txt  Screenshots  TODO.txt
{% endhighlight %}
<strong>Do some magick</strong>
{% highlight bash %}
git filter-branch --subdirectory-filter android -- --all
Rewrite 33db13154330e9e7a33c0fb5c356eccb25a6edda (36/36)
Ref 'refs/heads/master' was rewritten
Ref 'refs/remotes/origin/master' was rewritten
Ref 'refs/remotes/origin/cities_release_1' was rewritten
WARNING: Ref 'refs/remotes/origin/master' is unchanged
Ref 'refs/remotes/origin/migrate_from_osgb36_to_wgs84' was rewritten
Ref 'refs/remotes/origin/migrate_to_catalyst' was rewritten
Ref 'refs/remotes/origin/reportemptyhomes' was rewritten
ls
Fix My Street  README.txt  Screenshots  TODO.txt
{% endhighlight %}
<strong>Change origin</strong>
{% highlight bash %}
git remote -v</p>
<p>origin	git@github.com:Kagee/fixmystreet.git (fetch)
origin	git@github.com:Kagee/fixmystreet.git (push)</p>
<p>git remote set-url origin git@github.com:Kagee/fiksgatami.git git@github.com:Kagee/fixmystreet.git</p>
<p>git remote -v</p>
<p>origin	git@github.com:Kagee/fiksgatami.git (fetch)
origin	git@github.com:Kagee/fiksgatami.git (push)
{% endhighlight %}
<strong>Push</strong>
{% highlight bash %}
hildenae@hildenae-laptop:~/tmp/fixmystreet$ git push origin master
Counting objects: 464, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (243/243), done.
Writing objects: 100% (464/464), 1.44 MiB, done.
Total 464 (delta 159), reused 428 (delta 158)
To git@github.com:Kagee/fiksgatami.git
 * [new branch]      master -&gt; master
{% endhighlight %}</p>
