---
layout: post
title: Use latexmk with xelatex
---

To compile a latex file with `latexmk` and `xelatex` you can use the following line of code

{% highlight bash %}
latexmk -pdf -e '$pdflatex=q/xelatex %O %S/' input.tex
{% endhighlight %}

 where `input.tex` is the latex file you want to compile.