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

Pour compiler le code Java on a deux options:

* Soit donner le PATHCLASS directement sur la ligne de compilation:

{% highlight bash %}
javac -cp "C:\xalan-j_2_7_1\xalan.jar" ApplyXPath.java
{% endhighlight %}

et après pour l'executer:

{% highlight bash %}
java -cp ".;C:\xalan-j_2_7_1\xalan.jar" ApplyXPath foo.xml /
{% endhighlight %}


* Ou soit definir les variables PATH et CLASSPATH dans le système d'exploitation. Les images montrent le cas pour Windows XP

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