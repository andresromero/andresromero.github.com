---
layout: post
title: El principio de Bonferroni
---

Muchos problemas de minería de datos buscan descubrir eventos poco usuales ocultos en cantidades masivas de datos. 

Supongamos que tenemos una cierta cantidad de datos entre los que buscamos la ocurrencia de ciertos eventos. Con frecuencia algunos eventos que podrían parecer altamente improbables pueden presentarse en datos completamente aleatorios, y si la cantidad de datos que colectemos aumenta su ocurrencia será aún más probable. Este tipo de ocurrencias son **engañosas** en el sentido de que no tienen otra causa en si que el simple hecho que una colección de datos puede tener características poco usuales que pueden parecer importantes pero que no lo son.

**El principio de Bonferroni** nos ayuda a distinguir estas ocurrencias aleatorias y evitar tratarlas como eventos reales. Para esto necesitamos primero calcular el número esperado de ocurrencias de los eventos que se están buscando suponiendo que los datos son completamente aleatorios. Si este número es claramente mayor al número de ocurrencias reales que se espera encontrar, entonces podemos concluir que cualquier cosa que encontremos será poco concluyente.

##Ejemplo

Supongamos que estamos en búsqueda de un grupo de maleantes. Tenemos información que nos hace creer que este grupo de maleantes se reúne periódicamente en un hotel para organizar sus planes. Ahora supongamos las siguientes aseveraciones:

1. Tenemos una lista de mil millones de personas consideradas como probables maleantes.
2. Cualquiera de estas personas visita un hotel un día de cada cien.
3. Un hotel en promedio alberga cien personas. Por lo tanto, existen 100,000 hoteles (lo suficiente para albergar al 1% entre los mil millones de personas que visitan un hotel en cualquier día).
4. Podemos examinar los registros correspondientes a los últimos mil días de los hoteles.

Para encontrar a los maleantes en estos datos debemos buscar a las personas que en dos días diferentes estuvieron en el mismo hotel. Supongamos primero que las personas se comportan de manera aleatoria, decidiendo con probabilidad 0.01 visitar un hotel en cualquier día dado. El grupo de personas que decidieron ir a un hotel, seleccionarán uno entre los $$10^5$$ que existen. 

####¿Qué tan probable es encontrar pares de personas que tomaron la misma decisión?

La probabilidad de que dos personas cualesquiera decidan ir a un hotel en cualquier día dado es 0.0001. La probabilidad de que además decidan ir al mismo hotel es esta probabilidad dividida entre $$10^5$$, así, la probabilidad de que dos personas visiten el mismo hotel es $$10^{-9}$$. La probabilidad de que se encuentren en el mismo hotel en dos días diferentes es el cuadrado de esta cifra: $$10^{-18}$$ (los hoteles no tienen que ser forzosamente los mismos en los dos días). La ocurrencia de este evento para un par de personas dado parecería altamente improbable.

####¿Cúantos eventos indicarían la presencia de maleantes?

El evento buscado es la concurrencia de un par de personas y un par de días (dos personas que se hayan encontrado en dos días diferentes en el mismo hotel). En el caso de valores grandes de $$n$$, la combinación $$\left(\begin{array}{c} n\\ 2 \end{array}  \right)$$ se aproxima a $$n^2/2$$, el número de pares posibles en una lista de mil millones de personas es entonces $$\left(\begin{array}{c} 10^9\\ 2 \end{array}  \right) = 5 \times 10^{17}$$. 

Además, el número de pares de días en una lista de mil días es $$\left(\begin{array}{c} 1000\\ 2 \end{array}  \right) = 5 \times 10^{5}$$. El número esperado de eventos que indicarían la presencia de maleantes sería entonces el producto de el número de pares de personas, el número de pares de días y la probabilidad de que un par de personas y un par de días sea una instancia del comportamiento que estamos buscando. Este número es

$$
\begin{equation}
    5 \times 10^{17} \times 5 \times 10^{5} \times 10^{-18} = 250,000
\end{equation}
$$

Lo que nos haría creer que un cuarto de millón de personas tiene un comportamiento atípico parecido al de un maleante (aunque no tengan nada qeu ver). Si entre este grupo de un cuarto de millón se encontraran realmente diez maleantes, sería muy difícil para la policía con esta información poderlos encontrar.

####¿Qué pasaría si se incrementara el número de días de observación a 2000?

El número de pares de personas seguiría siendo el mismo, así como la probabilidad de que dos personas se encuentren en un mismo hotel en dos días diferentes, lo que cambiaría son el número de posibles pares de días: $$\left(\begin{array}{c} 2000\\ 2 \end{array}  \right) = 2 \times 10^{6}$$, por lo que

$$
\begin{equation}
    5 \times 10^{17} \times 2 \times 10^{6} \times 10^{-18} = 1,000,000
\end{equation}
$$

Es decir el número de eventos se cuadruplicaría.

####¿Si el número de personas observadas fuese 2 mil millones (incrementando también el número de hoteles a 200,000)?

La probabilidad de que dos personas cualesquiera decidan ir a un hotel el mismo día sigue siendo 0.0001. La probabilidad de que se encuentren en el mismo hotel es ahora $$\frac{1}{2 \times 10^5} = 5 \times 10^{-6}$$. Así la probabilidad de que dos personas visiten el mismo hotel es $$5 \times 10^{-10}$$, y de que se encuentren dos veces en un mismo hotel $$2.5 \times 10^{-19}$$.

El número de pares de personas también se incrementa a $$\left(\begin{array}{c} 2 \times 10^9\\ 2 \end{array}  \right) = 2 \times 10^{18}$$. Así

$$
\begin{equation}
    2 \times 10^{18} \times 5 \times 10^{5} \times 2.5 \times 10^{-19} = 250,000
\end{equation}
$$

## Ejemplo 2

Supongamos que conocemos las compras en una cadena de supermercados de 100 millones de personas. **Cada persona va al supermercado 100 veces al año y compra 10 productos de una lista de 1000 posibles** que el supermercado vende. Se cree que un par de terroristas compraría exactamente el mismo conjunto de productos (los ingredientes para producir una bomba quizás) en algún momento del año. Si buscamos por todos los pares de compradores que han comprado el mismo conjunto de productos, **¿podríamos esperar que algunos de eso compradores sean en realidad terroristas?**

Si el supermercado ofrece 1000 productos diferentes, tenemos un total de **$$1000!/(990! \times 10!)$$** posibles listas de diez productos, esto es posible aproximarlo como $$1000^{10}/10!$$.

Suponiendo que cada cliente que va al supermercado escoge los productos que se lleva de forma aleatoria, la probabilidad de que dos personas se lleven exactamente la misma lista de productos es entonces 

$$
\begin{equation}
    \left( \frac{1}{\left(\begin{array}{c} 1000\\ 10 \end{array}\right)} \right)^2
\end{equation} \approx \left(\frac{1}{1000^{10}/10!}\right)^2 = 1.3168 \times 10^{-47}
$$,

lo que parecería altamente improbable.

En 100 millones de personas tenemos aproximadamente $$5 \times 10^{15}$$ pares de personas. En cada par de personas podemos comparar sus cien listas de productos por lo que

$$
\begin{equation}
5 \times 10^{15} \times 10^4 \times 1.3168 \times 10^{-47} = 6.584 \times 10^{-28}
\end{equation}
$$

lo que indicaría que sí es poco probable que dos personas escojan los mismos productos de forma aleatoria.