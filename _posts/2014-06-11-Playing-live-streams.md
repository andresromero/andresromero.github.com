---
layout: masonry
title: Playing live RTMP streams
---

## About rtmpSnoop 

I've just found Andrea Fabrizi's script which allows to recover the RTMP parameters to play live streams in media players such as VLC, this thing interests me because I want to play this kind of streams on my Raspberry PI using Omxplayer.

The program is called `rtmpSnoop` and you can find it on [GitHub](https://github.com/andreafabrizi/rtmpSnoop).

## Instructions

Once you have cloned `rtmpSnoop` you just need to run the script (as root)

{% highlight bash %}
./rtmpSnoop.py -i wlp18s0 --out-rtmpdump # as root
{% endhighlight %}

and open a webpage where a RTMP live stream is playing, then the script will print something like this

{% highlight bash %}
rtmpSnoop v0.2.1 - The RTMP Sniffer!
Andrea Fabrizi - andrea.fabrizi@gmail.com

Starting sniffing on wlp18s0...

* RTMP Stream found!
*************************************
rtmpdump -r 'rtmp://live1.fifaembed.com:1935/live?wmsAuthSign=c2VydmVyX3RpbWU9Ni8xMS8yMDE0IDEwOjQ5OjA1IFBNJmhhc2hfdmFsdWU9QVF6bnQ1aHNEcHMrVVExRkU5aE5NZz09JnZhbGlkbWludXRlcz0x/espnusa-hq' -a 'live?wmsAuthSign=c2VydmVyX3RpbWU9Ni8xMS8yMDE0IDEwOjQ5OjA1IFBNJmhhc2hfdmFsdWU9QVF6bnQ1aHNEcHMrVVExRkU5aE5NZz09JnZhbGlkbWludXRlcz0x/' -t 'rtmp://live1.fifaembed.com:1935/live?wmsAuthSign=c2VydmVyX3RpbWU9Ni8xMS8yMDE0IDEwOjQ5OjA1IFBNJmhhc2hfdmFsdWU9QVF6bnQ1aHNEcHMrVVExRkU5aE5NZz09JnZhbGlkbWludXRlcz0x/' -y 'espnusa-hq' -W 'http://p.jwpcdn.com/6/8/jwplayer.flash.swf' -p 'http://www.fifaembed.com' -f 'LNX 11,2,202,356' --live -o espnusa-hq
{% endhighlight %}

Here you just need to copy this string to play it with VLC (or Omxplayer):

{% highlight bash %}
rtmpdump -r 'rtmp://live1.fifaembed.com:1935/live?wmsAuthSign=c2VydmVyX3RpbWU9Ni8xMS8yMDE0IDEwOjQ5OjA1IFBNJmhhc2hfdmFsdWU9QVF6bnQ1aHNEcHMrVVExRkU5aE5NZz09JnZhbGlkbWludXRlcz0x/espnusa-hq' -a 'live?wmsAuthSign=c2VydmVyX3RpbWU9Ni8xMS8yMDE0IDEwOjQ5OjA1IFBNJmhhc2hfdmFsdWU9QVF6bnQ1aHNEcHMrVVExRkU5aE5NZz09JnZhbGlkbWludXRlcz0x/' -t 'rtmp://live1.fifaembed.com:1935/live?wmsAuthSign=c2VydmVyX3RpbWU9Ni8xMS8yMDE0IDEwOjQ5OjA1IFBNJmhhc2hfdmFsdWU9QVF6bnQ1aHNEcHMrVVExRkU5aE5NZz09JnZhbGlkbWludXRlcz0x/' -y 'espnusa-hq' -W 'http://p.jwpcdn.com/6/8/jwplayer.flash.swf' -p 'http://www.fifaembed.com' -f 'LNX 11,2,202,356' --live | vlc -
{% endhighlight %}