---
layout: post
status: publish
published: true
title: SyntaxHighlighter Evolved with highlight-range
date: 2010-07-07 19:08:18 +0200
categories:
- code
- english
- php
- wordpress
tags: []
---
<b>Update: As of SyntaxHighlighter Evolved v. 3.0.0 this functionality is included in the plugin.</b>

One of the first plugins i installed for this brand new WordPress 
was <a href="http://www.viper007bond.com/wordpress-plugins/syntaxhighlighter/">
SyntaxHighlighter Evolved</a>. I love to code, and knew i would find 
a use for it. To test it i used a large C++ file 
from <s><del><a href="#http://cpp.snippets.org/code/">cpp.snippets.org</a></del></s> and 
began <a href="http://en.support.wordpress.com/code/posting-source-code/">testing</a>.

<code>Highlight</code> worked fine, but i i didn't support 
highlighting a range of lines. This might not be so useful, 
as you usually want to highlight small sections, but i rewrote 
syntaxhighlighter.php to support ranges.

<!--more-->
{% highlight php %}
[code language="php" firstline="740" gutter="true" highlight="748-761,765"][/code]
{% endhighlight %}

This expandes into

{% highlight html %}
<pre class="brush: php; auto-links: false; first-line: 740; gutter: true;
highlight: [765,748,749,750,751,752,753,754,755,756,757,758,759,760,761];
html-script: false; light: false; pad-line-numbers: false;
smart-tabs: true; tab-size: 4; toolbar: true; wrap-lines: true;"></pre>
{% endhighlight %}

<p>after beeing parsed by my (line 8-21,25) changes</p>
{% highlight php linenos %}
// Sanitize row highlights
if ( false != $atts['highlight'] ) {
        if ( false === strpos( $atts['highlight'], ',' ) && false === strpos( $atts['highlight'], '-' ) ) {
                $atts['highlight'] = (int) $atts['highlight'];
        } else {
                $highlights = explode( ',', $atts['highlight'] );
                foreach ( $highlights as $key => $highlight ) {
                        // if this value is a range
                        if (FALSE !== strpos($highlight, '-',1)) {
                                // we require 1 digit before the dash,
                                // if not we ignore it and pass it on
                                $range = explode('-', $highlight);
                                // Around here we should probably try to cast
                                // to int and if-check to sanitize the values
                                // loop over the range and add it to highlights
                                for(;$range[0] <= $range[1]; $range[0]++){
                                        $highlights[] = $range[0];
                                }
                                // unset the current (range-type) highlight
                                unset($highlights[$key]);
                        } else {
                                $highlights[$key] = (int) $highlight;
                                if ( empty($highlights[$key]) )
                                        unset($highlights[$key]);
                        }
                }
                $atts['highlight'] = implode( ',', $highlights );
        }
}
{% endhighlight %}

New <s><del><a href="#http://blog.hild1.no/quaseer/wp-content/uploads/code/syntaxhighlighter/syntaxhighlighter.highlight_range.phps">syntaxhighlighter.php</a></del></s> with 
highlight-range-code based on SyntaxHighlighter Evolved version 2.3.8

See also [Syntaxhighlighter Evolved with inline-highlight]({% post_url 2010-07-12-syntaxhighlighter-evolved-with-inline-highlight %})
