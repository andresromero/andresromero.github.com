---
layout: post
title: How to stream the sound from any application in Linux using Pulseaudio.
---
First we need to install and configure `icecast2`,  then we initialize it in Ubuntu 13.04 with:

{% highlight bash %}
sudo service icecast2 start
{% endhighlight %}

Following these [instructions](http://askubuntu.com/questions/60837/record-a-programs-output-with-pulseaudio) it is possible to initialize a sink. To do this, in a terminal we enter

{% highlight bash %}
pacmd
{% endhighlight %}

(this is the CLI of the PulseAudio-Server) and then we use

{% highlight bash %}
list-sink-inputs
{% endhighlight %}
to find the index of your input, for now on referred to as $INDEX.

To initialize the sink we do:

{% highlight bash %}
pactl load-module module-null-sink sink_name=steam
pactl move-sink-input $INDEX steam
{% endhighlight %}

And to launch the strem finally:
{% highlight bash %}
gst-launch-0.10 pulsesrc device=null.monitor ! audioconvert ! audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc bitrate=128 ! shout2send ip=localhost port=8000 password=hackme mount=example2.ogg
{% endhighlight %}.