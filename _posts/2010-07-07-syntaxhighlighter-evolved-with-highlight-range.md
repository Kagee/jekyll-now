---
layout: post
status: publish
published: true
title: SyntaxHighlighter Evolved with highlight-range
author: Anders Einar Hilden
author_login: hildenae
author_email: hildenae@gmail.com
excerpt: ! '<strong>Update: As of SyntaxHighlighter Evolved v. 3.0.0 this functionality
  is included in the plugin.</strong>


  One of the first plugins i installed for this brand new WordPress was <a href="http://www.viper007bond.com/wordpress-plugins/syntaxhighlighter/">SyntaxHighlighter
  Evolved</a>. I love to code, and knew i would find a use for it. To test it i used
  a large C++ file from <a href="http://cpp.snippets.org/code/">cpp.snippets.org</a>
  and began <a href="http://en.support.wordpress.com/code/posting-source-code/">testing</a>.


  <code>Highlight</code> worked fine, but i i didn''t support highlighting a range
  of lines. This might not be so useful, as you usually want to highlight small sections,
  but i rewrote syntaxhighlighter.php to support ranges.


'
wordpress_id: 55
wordpress_url: http://blog.hild1.no/?p=55
date: !binary |-
  MjAxMC0wNy0wNyAxOTowODoxOCArMDIwMA==
date_gmt: !binary |-
  MjAxMC0wNy0wNyAxNzowODoxOCArMDIwMA==
categories:
- code
- english
- php
- wordpress
tags: []
comments:
- id: 3
  author: Alex (Viper007Bond)
  author_email: viper@viper007bond.com
  author_url: http://www.viper007bond.com/
  date: !binary |-
    MjAxMC0wNy0xMSAwNDo1OTo0OCArMDIwMA==
  date_gmt: !binary |-
    MjAxMC0wNy0xMSAwMjo1OTo0OCArMDIwMA==
  content: Great idea! I'll include it in the next version. :)
---
<p><strong>Update: As of SyntaxHighlighter Evolved v. 3.0.0 this functionality is included in the plugin.</strong></p>
<p>One of the first plugins i installed for this brand new WordPress was <a href="http://www.viper007bond.com/wordpress-plugins/syntaxhighlighter/">SyntaxHighlighter Evolved</a>. I love to code, and knew i would find a use for it. To test it i used a large C++ file from <a href="http://cpp.snippets.org/code/">cpp.snippets.org</a> and began <a href="http://en.support.wordpress.com/code/posting-source-code/">testing</a>.</p>
<p><code>Highlight</code> worked fine, but i i didn't support highlighting a range of lines. This might not be so useful, as you usually want to highlight small sections, but i rewrote syntaxhighlighter.php to support ranges.</p>
<p><a id="more"></a><a id="more-55"></a></p>
<p>[code language="text" toolbar="true" gutter="false"]<br />
[code language=&quot;php&quot; firstline=&quot;740&quot; gutter=&quot;true&quot; highlight=&quot;748-761,765&quot;][/code]</p>
<p>This expandes into</p>
<p>[code language="html" toolbar="true" gutter="false"]<br />
&lt;pre class=&quot;brush: php; auto-links: false; first-line: 740; gutter: true;<br />
highlight: [765,748,749,750,751,752,753,754,755,756,757,758,759,760,761];<br />
html-script: false; light: false; pad-line-numbers: false;<br />
smart-tabs: true; tab-size: 4; toolbar: true; wrap-lines: true;&quot;&gt;<br />
[/code]</p>
<p>after beeing parsed by my (highlighted) changes</p>
<p>[code language="php" wraplines="true" autolinks="false" firstline="740" gutter="true" highlight="748-761,765" htmlscript="false" light="false" padlinenumbers="false" smarttabs="true" tabsize="4" toolbar="true"]<br />
// Sanitize row highlights<br />
if ( false != $atts['highlight'] ) {<br />
@h@        if ( false === strpos( $atts['highlight'], ',' ) &amp;&amp; false === strpos( $atts['highlight'], '-' ) ) {<br />
                $atts['highlight'] = (int) $atts['highlight'];<br />
        } else {<br />
                $highlights = explode( ',', $atts['highlight'] );</p>
<p>                foreach ( $highlights as $key =&gt; $highlight ) {<br />
                        // if this value is a range<br />
                        if (FALSE !== strpos($highlight, '-',1)) {<br />
                                // we require 1 digit before the dash,<br />
                                // if not we ignore it and pass it on<br />
                                $range = explode('-', $highlight);<br />
                                // Around here we should probably try to cast<br />
                                // to int and if-check to sanitize the values<br />
                                // loop over the range and add it to highlights<br />
                                for(;$range[0] &lt;= $range[1]; $range[0]++){<br />
                                        $highlights[] = $range[0];<br />
                                }<br />
                                // unset the current (range-type) highlight<br />
                                unset($highlights[$key]);<br />
                        } else {<br />
                                $highlights[$key] = (int) $highlight;<br />
                                if ( empty($highlights[$key]) )<br />
                                        unset($highlights[$key]);<br />
                        }<br />
                }</p>
<p>                $atts['highlight'] = implode( ',', $highlights );<br />
        }<br />
}<br />
[/code]</p>
<p>New <a href="http://blog.hild1.no/quaseer/wp-content/uploads/code/syntaxhighlighter/syntaxhighlighter.highlight_range.phps">syntaxhighlighter.php</a> with highlight-range-code based on SyntaxHighlighter Evolved version 2.3.8</p>
<p>See also <a href="http://blog.hild1.no/2010/07/syntaxhighlighter-evolved-with-inline-highlight/">Syntaxhighlighter Evolved with inline-highlight</a></p>
