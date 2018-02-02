---
layout: post
status: publish
published: true
title: SyntaxHighlighter Evolved with inline-highlight
author: Anders Einar Hilden
author_login: hildenae
author_email: hildenae@gmail.com
excerpt: ! 'After i first posted code for highlight-range i made some small changes
  to the code in the post as i found better ways of doing things. When i inserted
  new lines it messed with my highlighting. Inspired by pastebin.com, i wrote a couple
  of lines that let me specify with a marker in the code (and not by line-number)
  what line should be highlighted.


  <strong>Update:</strong> Added @hr@ for inline-ranges.

'
wordpress_id: 158
wordpress_url: http://blog.hild1.no/?p=158
date: !binary |-
  MjAxMC0wNy0xMiAwMzowMDo1NSArMDIwMA==
date_gmt: !binary |-
  MjAxMC0wNy0xMiAwMTowMDo1NSArMDIwMA==
categories:
- code
- english
- php
- wordpress
tags: []
comments: []
---
<p>After i first posted code for highlight-range i made some small changes to the code in the post as i found better ways of doing things. When i inserted new lines it messed with my highlighting. Inspired by pastebin.com, i wrote a couple of lines that let me specify with a marker in the code (and not by line-number) what line should be highlighted.</p>
<p><strong>Update:</strong> Added @hr@ for inline-ranges.<br />
<a id="more"></a><a id="more-158"></a><br />
The second codeblock is inside a shortcode similar to this:</p>
<p>[code language="plain"]<br />
[code language=&quot;php&quot; firstline=&quot;736&quot; gutter=&quot;true&quot; highlight=&quot;&quot;]<br />
[/code]</p>
<p>All the highlighting is done by @hr@-tags on line 740 and 761. Lines 747, 751 and 754 are prefixed with @h@ to show that single lines inside a (possibly) large highlighted range can be excluded. Both marker tags are removed and do not appear when displayed or in code-view.</p>
<p>[code language="php" firstline="736" gutter="true" highlight=""]<br />
        // Automatically enable &quot;htmlscript&quot; for certain brushes<br />
        //if ( false === $atts['html-script'] &amp;&amp; in_array( $lang, apply_filters( 'syntaxhighlighter_htmlscriptbrushes', array( 'php' ) ) ) )<br />
        //  $atts['html-script'] = 'true';</p>
<p>@hr@        // Detect and add inline highlights (@h@) and ranges (@hr@)<br />
        $codelines = explode(&quot;n&quot;, $code);<br />
        $h_marker = '@h@'; $h_marker_length = strlen($h_marker);<br />
        $h_range = '@hr@';<br />
        $atts['firstline'] = (int) $atts['firstline']; // sanitize firstline as we need it<br />
        $hra = false; $h = false;<br />
        foreach($codelines as $linenum =&gt; $line) { // could have used &amp;$line, but that is php5-only<br />
@h@            if($h_marker == substr($line, 0, $h_marker_length)) {<br />
                // could have used &quot;$line =&quot; in php<br />
                $codelines[$linenum] = substr($line,$h_marker_length, (strlen($line) - $h_marker_length));<br />
                $h = true;<br />
@h@            } else if($h_range == substr($line, 0, 4)) {<br />
                $hra = !$hra; // we swap on/of ever time we detect the tag<br />
                $codelines[$linenum] = substr($line,4); //, (strlen($line) - 4));<br />
@h@            }<br />
            if($h xor $hra) { // we use xor so we can use a @h@ to escape a active $hra<br />
                $atts['highlight'] = ($atts['highlight'] == false) ?<br />
                    ($linenum  + $atts['firstline'] -1 ) :<br />
                    $atts['highlight'] . ',' . ($linenum  + $atts['firstline'] -1 );<br />
            }<br />
            $h = false;<br />
        }<br />
@hr@        $code = implode(&quot;n&quot;,$codelines);</p>
<p>        // Sanitize row highlights<br />
        if ( false != $atts['highlight'] ) {<br />
[/code]</p>
<p>New <a href="http://blog.hild1.no/quaseer/wp-content/uploads/code/syntaxhighlighter/syntaxhighlighter.inline_highlight.phps">syntaxhighlighter.php</a> with the inline-highlight-code based on SyntaxHighlighter Evolved version 2.3.8</p>
<p>New <a href="http://blog.hild1.no/quaseer/wp-content/uploads/code/syntaxhighlighter/syntaxhighlighter.inline_highlight.highlight_range.phps">syntaxhighlighter.php</a> with the inline-highlight and highlight-range-code based on SyntaxHighlighter Evolved version 2.3.8</p>
