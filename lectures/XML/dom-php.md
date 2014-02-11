---
layout: masonry
title: DOM via PHP
---
Langage de script pour création de pages Web dynamiques, un fichier PHP est un fichier HTML avec du code PHP.

[**Download examples**](php-dom-examples.tar.gz)

{% highlight php %}
<html>
<body>
<?php
	$i = 1;
	if(1==$i){
		echo "i est 1 <br>";
	}else{
		echo "i n'est pas 1 <br>";
	};

	while($i < 5)
	{
		echo "i est $i<br>";
		$i += 1;	
	}

	do
	{ 
		echo "i is $i<br>";
		$i--;
	}while ($i > 0);
	
	echo (0==$i ? "i est a nouveu 0" : "i n’est pas 0");

	
?>
</body>
</html>
{% endhighlight %}

##Exemple: formulaires et PHP

{% highlight html %}
<html>
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
</head>
<body>
	<form action="action.php" method="post">
	<p>Votre nom : <input type="text" name="nom" /></p>
	<p>Votre âge : <input type="text" name="age" /></p>
	<p><input type="submit" value="OK"></p>
	</form>
</body>
</html>
{% endhighlight %}

{% highlight php  %}
<html>
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
</head>
<body>
	Bonjour,
	<?php
		 echo htmlspecialchars($_POST['nom']);
	?>.
	Tu as 
	<?php echo (int)$_POST['age']+2; ?>
	ans.
</body>
</html>
{% endhighlight %}

##Lecture d'un fichier XML et sélection d'éléments avec PHP

### Exemple :
{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<books>
<book>
	<author>Jack Herrington</author>
	<title>PHP Hacks</title>
	<publisher>O'Reilly</publisher>
</book>
<book>
	<author>Jack Herrington</author>
	<title>Podcasting Hacks</title>
	<publisher>O'Reilly</publisher>
</book>
<book>
	<author>Jack Herrington</author>
	<title>New Hacks</title>
	<publisher>O'Reilly</publisher>
</book>
</books>
{% endhighlight %}

{% highlight php  %}
<!-- Lecture de document, et sélection d'éléments -->
<?php
$doc = new DOMDocument();
$doc->load('books.xml');

$books = $doc->getElementsByTagName("book");

foreach ($books as $book) {
	$authors = $book->getElementsByTagName("author");
	$author =$authors->item(0)->nodeValue;

	$publishers = $book->getElementsByTagName("publisher");
	$publisher = $publishers->item(0)->nodeValue;

	$titles = $book->getElementsByTagName("title");
	$title = $titles->item(0)->nodeValue;	

	echo "$title - $author - $publisher<br>";
};
?>
{% endhighlight %}

## Création et écriture des documents

{% highlight php  %}
<!-- Création de document, et écriture-->
<?php
$books = array();
$books [] = array(
		'title' => 'PHP Hacks',
		'author' => 'Jack Herrington',
		'publisher' => "O'Reilly"
	);
$books [] = array(
		'title' => 'Podcasting Hacks',
		'author' => 'Jack Herrington',
		'publisher' => "O'Reilly"
	);

$doc = new DOMDocument("1.0", "UTF-8");
$doc->formatOutput = true;

$r = $doc->createElement("books");
$doc->appendChild($r);

foreach ($books as $book) {
	$b = $doc->createElement("book");	
	
	$author = $doc->createElement("author");
	$author->appendChild(
		$doc->createTextNode($book['author'])
	);	
	$b->appendChild( $author );

	$title = $doc->createElement( "title" );
	$title->appendChild(
	$doc->createTextNode( $book['title'] )
	);
	$b->appendChild($title);

	$publisher = $doc->createElement("publisher");
	$publisher->appendChild(
	$doc->createTextNode($book['publisher'])
	);
	$b->appendChild($publisher);
	$r->appendChild($b);
};

echo $doc->saveXML();
?>
{% endhighlight %}

## Evaluation de requêtes XPath

### Exemple: compter le nombre de livres écrits par un auteur

#### Version sans XPath
{% highlight php  %}
<!-- Compter le nobre de livres écrits par un auteur sans XPath-->
<?php
$doc = new DOMDocument();
$doc->load('books.xml');

$author = 'Jack Herrington';
$total = 0;
$elements = $doc->getElementsByTagName("author");
foreach ($elements as $element) {
	if($element->nodeValue==$author)
	{
		$total++;
	}
}
echo "Auteur $author a ecrit $total livres en total<br>";
?>
{% endhighlight %}

#### Avec XPath (version 1)
{% highlight php  %}
<!-- Compter le nobre de livres écrits par un auteur avec XPath-->
<?php
$author = 'Jack Herrington';

$doc = new DOMDocument();
$doc->load('books.xml');

$xpath = new DOMXPath($doc);
$query = "//book[author='$author']";
$result = $xpath->query($query);
$nbooks = 0;
foreach ($result as $element) {
	$nbooks++;
}
echo "$nbooks";
?>
{% endhighlight %}

#### Avec XPath (version 2)
{% highlight php  %}
<!-- Compter le nobre de livres écrits par un auteur avec XPath V2-->
<html>
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
</head>
<body>
	<?php
		$author = 'Jack Herrington';

		$doc = new DOMDocument();
		$doc->load('books.xml');

		$xpath = new DOMXPath($doc);
		$query = "count(//book[author='$author'])";
		$nbooks = $xpath->evaluate($query);

		echo "L'auteur $author a écrit $nbooks en total.<br>";
	?>
</body>
</html>

{% endhighlight %}





