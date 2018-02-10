---
layout: post
status: publish
published: true
title: SyntaxHighlighter Evolved with inline-highlight
date: 2010-07-12 03:00:55 +0200
categories:
- code
- english
- php
- wordpress
tags: []
comments: []
---
After i first posted code for highlight-range i made some small 
changes to the code in the post as i found better ways of doing 
things. When i inserted new lines it messed with my highlighting. 
Inspired by pastebin.com, i wrote a couple of lines that let me 
specify with a marker in the code (and not by line-number) what 
line should be highlighted.

<strong>Update:</strong> Added ```@hr@``` for inline-ranges.
<!--more-->
The second codeblock is inside a shortcode similar to this:

{% highlight text %}
[code language="php" firstline="736" gutter="true" highlight=""]
{% endhighlight %}

All the highlighting is done by ```@hr@```-tags on line 4 and 25. 
Lines 11, 15 and 18 are prefixed with ```@h@``` to show that single 
lines inside a (possibly) large highlighted range can be excluded. 
Both marker tags are removed and do not appear when displayed or 
in code-view.

{% highlight php linenos %}
// Automatically enable "htmlscript" for certain brushes
//if ( false === $atts['html-script'] && in_array( $lang, apply_filters( 'syntaxhighlighter_htmlscriptbrushes', array( 'php' ) ) ) )
//  $atts['html-script'] = 'true';
@hr@  // Detect and add inline highlights (@h@) and ranges (@hr@)
$codelines = explode("n", $code);
$h_marker = '@h@'; $h_marker_length = strlen($h_marker);
$h_range = '@hr@';
$atts['firstline'] = (int) $atts['firstline']; // sanitize firstline as we need it
$hra = false; $h = false;
foreach($codelines as $linenum => $line) { // could have used &$line, but that is php5-only
  @h@  if($h_marker == substr($line, 0, $h_marker_length)) {
  // could have used "$line =" in php
  $codelines[$linenum] = substr($line,$h_marker_length, (strlen($line) - $h_marker_length));
  $h = true;
  @h@  } else if($h_range == substr($line, 0, 4)) {
    $hra = !$hra; // we swap on/of ever time we detect the tag
    $codelines[$linenum] = substr($line,4); //, (strlen($line) - 4));
  @h@  }
  if($h xor $hra) { // we use xor so we can use a @h@ to escape a active $hra
    $atts['highlight'] = ($atts['highlight'] == false) ? 
      ($linenum  + $atts['firstline'] -1 ) :
      $atts['highlight'] . ',' . ($linenum  + $atts['firstline'] -1 );
  }
  $h = false;
}
@hr@  $code = implode("n",$codelines);
// Sanitize row highlights
if ( false != $atts['highlight'] ) {
{% endhighlight %}

New <s><del><a href="#http://blog.hild1.no/quaseer/wp-content/uploads/code/syntaxhighlighter/syntaxhighlighter.inline_highlight.phps">syntaxhighlighter.php</a></del></s> with 
the inline-highlight-code based on SyntaxHighlighter 
Evolved version 2.3.8

New <s><del><a href="#http://blog.hild1.no/quaseer/wp-content/uploads/code/syntaxhighlighter/syntaxhighlighter.inline_highlight.highlight_range.phps">syntaxhighlighter.php</a></del></s> with 
the inline-highlight and highlight-range-code based on 
SyntaxHighlighter Evolved version 2.3.8

