---
layout: post
title:  Math documents for Kindle using Pandoc
---

{% highlight bash %}
    mkdir myfile-images #Create folder to store eqs images
    pandoc -s --gladtex <markdown_file.md> -o <htex_file.htex>
    gladtex -d myfile-images <htex_file.htex>
    pandoc --epub-metadata=metadata.xml -f html -t epub3 <html_file.html> -o <epub_file.epub>
{% endhighlight %}  

where `metadata.xml` contains

{% highlight xml %}
    <dc:rights>Creative Commons Non-Commercial Share Alike 3.0</dc:rights>
    <dc:language>en-US</dc:language>
{% endhighlight %} 

and finally convert from epub3 to mobi

{% highlight bash %}
   ebook-convert <epub_file.epub> <mobi_file.mobi> 
{% endhighlight %}  

