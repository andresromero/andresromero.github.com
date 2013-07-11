---
layout: post
title: Compressing a PDF in Linux
---

If you need to significantly reduce the size of a PDF in Linux you can try the following line of code:

{% highlight bash %}
gs -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -SOutputFile=/tmp/output.pdf input.pdf 
{% endhighlight %}

 where `input.pdf` and `output.pdf` are the input and output files.
