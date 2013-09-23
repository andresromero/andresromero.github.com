---
layout: post
title: Represening beliefs consistently
---

Let's use $$b(x)$$ to represent the strength of belief in (plausibility of) proposition $$x$$.

$$
\begin{array}{cc}
    0 \leq b(x) \leq 1 &  \\
    b(x) = 0 & x \mbox{ is definetely not true}\\
    b(x) = 1 & x \mbox{ is definetely true}\\
    b(x|y) & \mbox{strength of belief that } x \mbox{ is true given that we know } y \mbox{ is true}
\end{array}
$$

Desiredata:

* Strengths of belief are represented by real numbers.
* Qualitative correspondence with common sense.
* Consistency
    * If a conclusion can be reasoned in several ways, then each way should lead to the same answer.
    * The robot (analyzer) must always take into account all relevant evidence.
    * Equivalent states of knowledge are represented by equivalent plausibility assignments.
