---
layout: post
title: "My Adventures with Adafruit PiTFT displays"
categories: rpi
---
# Hello world!

How are you? 



---
layout: post
title: "nmap xml to csv original hostname"
categories: code nmap mcn english
---
# Hello world!


Make it alive:
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

# Links
https://www.adafruit.com/product/2315
http://lallafa.de/blog/2015/03/fbtft-setup-on-modern-raspbian/
https://github.com/notro/fbtft/wiki/Framebuffer-use
