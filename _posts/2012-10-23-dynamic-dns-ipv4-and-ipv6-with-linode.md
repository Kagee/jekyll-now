---
layout: post
title: Dynamic DNS (IPv4 and IPv6) with Linode
date: !binary |-
  MjAxMi0xMC0yMyAxODo1NjoxMyArMDIwMA==
date_gmt: !binary |-
  MjAxMi0xMC0yMyAxNjo1NjoxMyArMDIwMA==
categories:
- code
- english
- perl
---
Do you have have free dynamic DNS through no-ip.com?

> Your free host hildenae.no-ip.org, will expire in 7 days due to account inactivity.
>
> hildenae.no-ip.org was last updated on 
> &lt;some-datetime-in-the-past&gt;. 
> Free Dynamic DNS hosts must be updated by logging into your account 
> on our website and clicking update, this must be done every 30 
> days. If you are using the Dynamic Update Client and <strong>your 
> IP address has not changed within the past 30 days</strong>, you 
> must manually update it to prevent them from being removed from 
> our system.

Yeah. With a mostly static IP from my <a title="I love those guys - especially the IT department" href="http://english.hig.no/">school</a>, that started to get annoying after five or six times.

<!--more-->

<p>Did you know <a href="http://www.linode.com/">Linode</a> supplies <a href="http://www.linode.com/faq.cfm#do-you-host-dns">free DNS hosting</a> if you have a VPS with them? Well, now you do. Their DNS manager is also avalible via their API, and said API has a <a href="http://search.cpan.org/~mikegrb/WebService-Linode/lib/WebService/Linode.pm">CPAN module</a> avalible. I see a homebrewed solution comming up.</p>
<p>Linode has done most of the work for us - if you download and extract the module, you will find <a href="http://git.thegrebs.com/?p=WebService-Linode;a=blob_plain;f=examples/dyndns.pl;hb=HEAD">examples/dyndns.pl</a>. This example however only works on IPv4, and uses an external service to determine the address. I hate to <del datetime="2012-10-23T14:49:48+00:00">bother</del> rely on external services for things like getting IP addresses, and because we have proper IPv6 routing here, having a AAAA record for my IPv6 address is also important.</p>
<hr>
<h3>The code and stuff</h3>
<p>For the lazy of you, <a href="http://search.cpan.org/~sullr/Net-INET6Glue/">INET6Glue</a> will hotpatch LWP do support IPv6 requests,<br />
{% highlight perl %}
use Net::INET6Glue::INET_is_INET6;
{% endhighlight %}
and <a href="http://icanhazip.com">icanhazip.com</a> supports the lookup of IPv6 (and 4) adresses.<br />
{% highlight perl %}
my $pubip = get('http://icanhazip.com/') or exit 1;
{% endhighlight %}
</p>
<p>I however, preffer to ask the hardware directly. For the IPv4 adress<br />
{% highlight bash %}
my $pubip = `ip -o addr show eth1 | \
awk '/inet / { split($4,ipv4,"/"); print ipv4[1] }'
{% endhighlight %}
and for the <a href="http://en.wikipedia.org/w/index.php?title=IPv6_address&amp;oldid=512155295#Temporary_addresses" title="Wikipedia article about temporary IPv6 addresses">temporary IPv6 address</a><br />
{% highlight bash %}
my $pubip = `ip -o addr show eth1 |
    awk '/inet6.*temporary/ { split($4,ipv6,"/"); print ipv6[1] }'`;
{% endhighlight %}
</p>
<p>The default script only lets you update a single host, and not both A and AAAA records if they are defined, but that will have to be a task for another day.</p>
