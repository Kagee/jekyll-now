---
layout: post
title: "My Adventures with Adafruit PiTFT displays"
categories: rpi
---
# Make it alive:
dtoverlay=pitft22
dtparam=spi=on

(actual pixelsize (width is probably the widest, but not on 3.2" touch)
(rotation does not affect these values)
framebuffer_width=320
framebuffer_height=240

Rotate:
dtparam=rotate=<deg>
Default 90 (top of display on button side)
270 (top of display on header side)

Append "fbcon=map:10 fbcon=font:VGA8x8 logo.nologo" to 
/boot/cmdline.txt to set framebuffer 1 as console to 
get console on pitft during boot

Better/smaller fonts:
sudo apt-get install kbd
edit /etc/default/console-setup or sudo dpkg-reconfigure console-setup

CHARMAP="UTF-8"
CODESET="guess"
FONTFACE="Terminus"
FONTSIZE="6x12"


# Links
https://www.adafruit.com/product/2315
http://lallafa.de/blog/2015/03/fbtft-setup-on-modern-raspbian/
https://github.com/notro/fbtft/wiki/Framebuffer-use
https://github.com/notro/fbtft/wiki/Boot-console (see Boot console for smaller font on screen)
https://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt#72
