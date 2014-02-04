---
layout: masonry
title: Exercices TD 1 XML et Gestion des données sur Internet
---
## Utilisation de *xalan.jar* 

Xalan est un bibliotèque Java qui permet lancer des requettes XPath et appliquer les transformations XSLT à votre document. 

1. Installation de [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html?ssSourceSiteId=otnjp)
2. Téléchargement de [Xalan](http://mirrors.ircam.fr/pub/apache/xalan/xalan-j/binaries/xalan-j_2_7_1-bin.zip)
3. Decompresion du fichier xalan-j_2_7_1-bin.zip
4. Compiler l'exemple ApplyXPath
{% highlight bash %}
	javac ApplyXPath.java
{% endhighlight %}

Il faut donner definir les variables PATH et CLASSPATH dans le système d'exploitation.

![alt text][XalanWindows]

[XalanWindows]: /static/images/xalan.png "Xalan Variables Java"


### Exemple d'exécution de la requette **/** sur le fichier **foo.xml**

{% highlight bash %}
	java ApplyXPath foo.xml /
	Loading classes, parsing foo.xml, and setting up serializer
	Querying DOM using /
	<output>
	<doc>
	  <name first="David" last="Marston"/>
	  <name first="David" last="Bertoni"/>
	  <name first="Donald" last="Leslie"/>
	  <name first="Emily" last="Farmer"/>
	  <name first="Joseph" last="Kesselman"/>
	  <name first="Myriam" last="Midy"/>
	  <name first="Paul" last="Dick"/>
	  <name first="Stephen" last="Auriemma"/>
	  <name first="Scott" last="Boag"/>
	  <name first="Shane" last="Curcuru"/>
	</doc>
	</output>
{% endhighlight %}