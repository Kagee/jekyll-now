---
layout: post
status: publish
published: true
title: Using BankID (norwegian type) in Ubuntu 10.04
author: Anders Einar Hilden
author_login: hildenae
author_email: hildenae@gmail.com
excerpt: ! "<div class=\"alert alert-info\">\r\nUpdate: As of Ubuntu 10.10 this should
  not be nessesary, as OpenJDK in Ubuntu &gt;= 10.10 should work with BankID.\r\n</div>\r\nIn
  Ubuntu 10.04 (and probably onwards) OpenJDK Java and the Icedtea java plugin are
  the standard Java toolkit. <a href=\"https://www.bankid.no/Hjelp-og-nyttige-verktoy/Nyttige-verktoy/Test-din-BankID/\">BankID</a>
  works with OpenJDK <em>(just try installing Opera 10.10. Opera pre 10.5 use OpenJDK
  directly, without Icedtea)</em>, Icedtea is the troublemaker.\r\n"
wordpress_id: 11
wordpress_url: http://blog.hild1.no/?p=11
date: !binary |-
  MjAxMC0wNy0wNiAyMjowODoyMiArMDIwMA==
date_gmt: !binary |-
  MjAxMC0wNy0wNiAyMjowODoyMiArMDIwMA==
categories:
- bash
- code
- english
tags: []
comments: []
---
<div class="alert alert-info">
Update: As of Ubuntu 10.10 this should not be nessesary, as OpenJDK in Ubuntu &gt;= 10.10 should work with BankID.
</div>
<p>In Ubuntu 10.04 (and probably onwards) OpenJDK Java and the Icedtea java plugin are the standard Java toolkit. <a href="https://www.bankid.no/Hjelp-og-nyttige-verktoy/Nyttige-verktoy/Test-din-BankID/">BankID</a> works with OpenJDK <em>(just try installing Opera 10.10. Opera pre 10.5 use OpenJDK directly, without Icedtea)</em>, Icedtea is the troublemaker.<br />
<a id="more"></a><a id="more-11"></a></p>
<p>Sun Java has been pushed all the way into the Canonocal partner repository, that is not enabled as default. The following lines are a quick way to enable it and install java, even if the same is possible with lengthy GUI "click-here-then-there" tutorials.</p>
<p>[code language="bash" wraplines="false" autolinks="false" toolbar="false" gutter="false"]sudo add-apt-repository &quot;deb http://archive.canonical.com/ lucid partner&quot;<br />
sudo apt-get update<br />
sudo apt-get install sun-java6-plugin[/code]</p>
<p>Line one adds the Canonical Partner repository to you software sources. There should be no complications if it is already enabled. Line two updates the list of avalible packages, so that line three can find and install the package <code>sun-java6-plugin</code> and it's dependencies.</p>
<p>Sun Java should be the standard after this, if not, try to force it to be default with this line. And remember to restart you browser (or possibly restart your system)</p>
<p>[code language="bash" wraplines="false" gutter="false" toolbar="false"]sudo update-java-alternatives -s java-6-sun[/code] </p>
