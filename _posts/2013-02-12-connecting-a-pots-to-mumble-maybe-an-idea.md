---
layout: post
status: publish
title: Connecting a POTS to Mumble maybe? - an idea
date: !binary |-
  MjAxMy0wMi0xMiAwMDo0NDo0NSArMDEwMA==
date_gmt: !binary |-
  MjAxMy0wMi0xMSAyMjo0NDo0NSArMDEwMA==
---
<p>So, the problem: Moving from Skype (closed source) to Mumble for meetings, while still having the possibility to conference with the occasional user of a POTS (plain old telephone system)</p>
<!-- more -->
<p>Skype lets you call POTS. Skype has a API that, among other things, allow you to send a copy of a call to a file or TCP port, and receive audio from same. The same API can also make call, e.g to POTS.<br />
<a href="http://dev.skype.com/desktop-api-reference" title="http://dev.skype.com/desktop-api-reference" target="_blank">http://dev.skype.com/desktop-api-reference</a></p>
<p>Pacat/parec allows you to use files as sources and sinks for PulseAudio. (which again can be used by Mumble)<br />
<a href="http://linux.die.net/man/1/pacat" title="http://linux.die.net/man/1/pacat" target="_blank">http://linux.die.net/man/1/pacat</a></p>
<p>Scripts must be written, tests must be done!</p>
