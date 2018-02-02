---
layout: post
status: publish
published: true
title: Enabling VNC and disabling desktop effects from the command line
author: Anders Einar Hilden
author_login: hildenae
author_email: hildenae@gmail.com
excerpt: ! 'Don''t you just hate those day when you really need to access the desktop
  of a machine, but forgot or just never activated remote desktop?

'
wordpress_id: 314
wordpress_url: http://blog.hild1.no/?p=314
date: !binary |-
  MjAxMS0wMi0wNSAxMjozODoxMyArMDEwMA==
date_gmt: !binary |-
  MjAxMS0wMi0wNSAxMDozODoxMyArMDEwMA==
categories:
- bash
- code
- english
tags: []
comments:
- id: 4
  author: Enabling VNC and disabling desktop effects from the command line at Moshwire.com
  author_email: ''
  author_url: http://www.moshwire.com/2011/02/enabling-vnc-and-disabling-desktop-effects-from-the-command-line/
  date: !binary |-
    MjAxMS0wMi0wNiAxMTo1NDo0OSArMDEwMA==
  date_gmt: !binary |-
    MjAxMS0wMi0wNiAwOTo1NDo0OSArMDEwMA==
  content: ! '[...] You can find it here. [...] '
---
<p>Don't you just hate those day when you really need to access the desktop of a machine, but forgot or just never activated remote desktop?<br />
<a id="more"></a><a id="more-314"></a><br />
Fear not, the following lines will let you activate it from a SSH-shell:</p>
<p>[code language="bash" light="true"]<br />
# display number, assuming 0<br />
display=0</p>
<p># get the machine-id<br />
read -r machineid &lt; /var/lib/dbus/machine-id</p>
<p># source the right file under .dbus to set the needed variables<br />
. &quot;$HOME/.dbus/session-bus/$machineid-$display&quot;</p>
<p># export the variables sourced from that file<br />
export DBUS_SESSION_BUS_ADDRESS DBUS_SESSION_BUS_PID DBUS_SESSION_BUS_WINDOWID</p>
<p># Run gconftool-2:</p>
<p># enable desktop sharing<br />
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true</p>
<p># disable &quot;You must confirm each access to this machine&quot;<br />
gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false</p>
<p># enable &quot;Allow other users to control your desktop&quot;<br />
gconftool-2 -s -t bool /desktop/gnome/remote_access/view_only false<br />
[/code]</p>
<p><strong>Remeber to set a password after you log in (afaik you can't set this from cli)</strong></p>
<p>I use the propiatary ATI drivers, and because of a bug i have to disable desktop effects, else the VNC windows will only show me a static desktop and no updates:</p>
<p>[code language="bash" light="true"]<br />
# disable desktop effects (if your desktop<br />
gconftool -s -t string /desktop/gnome/applications/window_manager/current /usr/bin/metacity<br />
gconftool -s -t string /desktop/gnome/applications/window_manager/default /usr/bin/metacity</p>
<p>sudo reboot<br />
[/code]</p>
<h3>Sources</h3>
<p><a href="https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126">https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126</a><br />
<a href="http://ubuntuforums.org/showthread.php?t=1518231">http://ubuntuforums.org/showthread.php?t=1518231</a></p>
