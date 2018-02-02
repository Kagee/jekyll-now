---
layout: post
title: "Perl regexp oneliners and UTF-8"
date: 2016-11-12 22:00:00 +0000
comments: true
categories: code perl regexp english 
published: 2016-11-12 22:00:00 +0000
---
For my project to  [find as many .no domains as possible](https://github.com/Kagee/make-clean-no-list),
I needed a regexp for extracting valid domains. This task is made
more fun by the inclusion of Norwegian and Sami characters in the
set of [valid characters.](https://www.norid.no/no/domeneregistrering/idn/idn_nyetegn/)

<!-- more -->

In addition to ```[a-z0-9\-]```, valid dot-no domains can contain the 
Norwegian ```æ``` (ae), ```ø``` (o with stroke) and ```å``` (a with 
ring above) ([Stargate](https://en.wikipedia.org/wiki/Stargate_SG-1), 
anyone?) and a number of Sami characters. ```ŧ``` (t with stroke), 
 ```ç``` (c with cedilla) and ```ŋ``` (simply called "eng") are some 
of my favourites.

The following code will print only the first match per line, and 
uses ```ŧ``` directly in the regexp.

```bash
        echo "fooŧ.no baŧ.no" | \
        perl -ne 'if(/([a-zŧ]{2,63}\.no)/ig) { print $1,"\n"; }'
        fooŧ.no
```
If we replace ```if``` with ```while``` we will print any match found
in the whole line.
```bash
echo "fooŧ.no baŧ.no" | \
perl -ne 'while(/([a-zŧ]{2,63}\.no)/ig) { print $1,"\n"; }'
fooŧ.no
baŧ.no
```

Because I'm afraid the regexp (specifically the non-ASCII characters) 
may be mangled by being saved and moved between systems, I want to 
write the Norwegian and Sami characters using their Unicode code points. 
Perl has support for this using ```\x{<number>}``` (see 
[perl unicode](http://perldoc.perl.org/perlunicode.html#Unicode-Regular-Expression-Support-Level))

```bash
echo "fooŧ.no baŧ.no" | \
perl -CSD -ne 'while(/([a-z\x{167}]{2,63}\.no)/ig) { print $1,"\n"; }'
fooŧ.no
baŧ.no
```
When using code points, I have to specify ```-CSD``` for the matching 
to work. I am not really sure why this is required. If you can explain,
please comment or tell my by other means. As you can read in
[perlrun](http://perldoc.perl.org/perlrun.html#Command-Switches),
 ```-CSD``` specifies that ```STDIN```, ```STDOUT```, ```STDERR``` and all input and 
output streams should be treated as being UTF-8. 

Another problem is that if this last solution is is fed invalid UTF-8, 
it will die fatally and stop processing input.

```bash
Malformed UTF-8 character (fatal) at -e line 1, <> line X.
```

To prevent this happening I currently sanitize my dirty input using 
 ```iconv -f utf-8 -t utf-8 -c```. If you have a better solution for 
this, Perl or otherwise, please tell me!.

A simple regexp would match the valid characters for a length between
2 and 63 followed by ```.no```. However, I wanted *only* and *all* 
"domains under .no" as counted by Norid in their 
[statistics](https://www.norid.no/no/statistikk/domener/). 
Norids definition of "domains under .no" are all the domains directly 
under ```.no```, but *also* domains under *category domains* i.e. 
```ohv.oslo.no``` and ```ola.priv.no```. To get comparable results, I 
have to collect both ```*.no``` and ```*.<category domain>.no``` 
domains when scraping data.

The resulting "oneliner" I use is 
[this…](https://github.com/Kagee/make-clean-no-list/blob/master/scraper/regexp_dotno).
It once was a oneliner, but with more than 10k characters in the 
regexp it was hard to manage. The resulting script builds up a regexp 
that is valid for all Norwegian domains using a list of valid category 
domains, all valid characters and other rules for .no domains.
