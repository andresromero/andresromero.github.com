---
layout: post
title: La importancia de las palabras en los documentos
---

En algunos aplicaciones de minería de datos podemos encontrarnos con el problema de categorizar un documento (o una secuencia de palabras) con un tópico. Típicamente los tópicos son identificados encontrando las palabras especiales que caracterizan a un documento. Por ejemplo, los artículos sobre política muestran una tendencia a hablar sobre *elecciones*, *partidos*, *candidato*, *votos*, etc.

Una vez que hemos clasificado los documentos y determinado cuales son los que hablan de política, no es difícil darse cuenta que las palabras del tipo que hemos hablando aparecen en realidad con poca frecuencia. Hasta después de haber clasificado por temas una serie de documentos es dificil poder decir que estas palabras son características.

Los sistemas de clasificación por lo general recorren los documentos y buscan las palabras más significativas. Un primer paso sería pensar que las palabras que aparecen más frecuentemente en un documento son las más importantes, sin embargo esta suposición es exactamente opuesta a la verdad. Las palabras más comunes con mucha probabilidad serán los artículos, preposiciones o conjunciones. Palabras como *el*, *de*, *y*, *o*, etc. Este tipo de palabras sirven para hilar las ideas pero en realidad no contienen un significado por sí mismas. Este tipo de palabras (llamadas **palabras de parada**) son las más comunes en cualquier idioma y por lo general son removidas de los documentos antes de intentar clasificarlos.

Las palabras relacionadas con el tópico son por lo general raras, sin embargo no todas las palabras raras que aparecen en un documento estan necesariamente relacionadas con el tópico. Existen algunas palabras que son raras en sí pero que no indican nada útil sobre el tópico. La palabra *carabela* es rara (no aparece en muchos textos) y es un fuerte indicador de que se trata de un texto que habla sobre el descubrimiento de América. 

La diferencia entre las palabras que nos dicen algo y las que no tiene que ver con la concentración de las palabras útiles en únos pocos documentos de cierto tipo (o relacionados con algún tema en particular).

Una medida formal de que tan concentrada esta una palabra en algunos pocos documentos es llamado **TF.IDF** (del inglés *Term Frequency times Inverse Document Frequency*). Supongamos que tenemos una colección de $$N$$ documentos. Definamos $$f_{ij}$$ a la *frecuencia* (número de apariciones) del término $$i$$ en el documento $$j$$. Así, la frecuencia del término es

$$
\begin{equation}
    TF_{ij} = \frac{f_{ij}}{\max_k f_{kj}}.
\end{equation}
$$

La frecuencia del término $$i$$ en el documento $$j$$ ($$f_{ij}$$) es normalizada dividiendola entre el número máximo de ocurrencias de cualquier término en el mismo documento (quizás sería conveniente remover primero las palabras de parada). Así, el término más utilizado en el documento $$j$$ recibe $$TF = 1$$.

El término *IDF* es definido de la siguiente manera. Supongamos que el término $$i$$ aparece en $$n_i$$ documentos en una colección de $$N$$ documentos. La frecuencia inversa del documento es $$IDF_i = \log_2(N/n_i)$$. Así, la medición $$TF.IDF$$ para el término $$i$$ en el documento $$j$$ es definida como $$TF_{ij} \times IDF_i$$. Los términos con TF.IDF más alta son los términos que mejor caracterizan el tópico de un documento.

####Ejemplo

Supongamos un repositorio de $$2^{20} = 1,048,576$$ documentos. Si la palabra $$w$$ aparece en $$2^{10}=1024$$ de estos, entonces $$IDF_w = \log_2(2^{20}/2^{10}) = 10$$. Si tenemos un documento $$j$$ en donde $$w$$ aparece 20 veces y ese es el máximo número de veces que cualquier palabra aparece en el documento (después de quitar las palabras de parada). Entonces el valor de $$TF_{wj} = 1$$, y la medición de TF.IDF para $$w$$ en el documento $$j$$ es 10.

####Ejemplo 2

Supongamos que tenemos un repositorio de diez millones de documentos.  

(a) ¿Cuál es el valor de IDF para una palabra que aparece en 40 documentos?

$$IDF_i = \log_2(N/n_i) = \log_2(10 \times 10^6 / 40) \approx 18 $$

(b) ¿Cuál es el valor de IDF para una palabra que aparece en 10,000 documentos?

$$IDF_i = \log_2(N/n_i) = \log_2(10 \times 10^6 / 1 \times 10^4) \approx 10 $$

####Ejemplo 3

Supongamos ahora un repositorio de 10 millones de documentos, la palabra $$w$$ aparece en 320 de ellos. En un documento en particular $$d$$, el máximo número de ocurrencias de una palabra es $$15$$. ¿Cuál es el valor aproximado de TF.IDF para $$w$$ si aparece (a) una vez, (b) cinco veces?

*Respuesta*: Primero estimamos el valor de $$IDF_w$$ como $$IDF_w = \log_2(10 \times 10^6 / 320) \approx 15$$. Ahora normalizamos el número de ocurrencias entre el número máximo de ocurrencias de una palabra en el documento y multiplicamos por $$IDF_w$$, así

$$
(a) TF_w = 1/15, \mbox{ por lo que TF.IDF} = \frac{1}{15} \times 15 = 1 \\
(b) TF_w = 5/15, \mbox{ por lo que TF.IDF} = \frac{5}{15} \times 15 = 5
$$

#Referencias
[Mining of Massive Datasets](http://books.google.fr/books?id=OefRhZyYOb0C)