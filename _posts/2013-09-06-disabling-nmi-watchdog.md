---
layout: post
title: Disable NMI watchdog for code profiling with Vtune or Oprofile in Linux
---

Just run the following command before launching VTune 

{% highlight bash %}
$ echo "0" | sudo tee /proc/sys/kernel/watchdog  
{% endhighlight %}