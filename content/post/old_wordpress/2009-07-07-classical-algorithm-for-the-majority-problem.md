---
title: Classical algorithm for the Majority Problem
author: Jice

date: 2009-07-07
url: /2009/07/classical-algorithm-for-the-majority-problem/
categories:
  - Informatique
  - Quantum Learning
tags:
  - machine learning
  - Majority problem
  - Perceptron
---
## Presentation of the problem :

<p style="text-align: justify;">
  The majority problem is equivalent to the perceptron learning. For each $$a \in \mathbb{Z}_n$$ define a function $$m_a : \mathbb{Z}_2^N \rightarrow \mathbb{Z}_2$$ :
</p>

<p style="text-align: center;">
  $$m_a(x)= \begin{cases} 1 & \text{ if } wt(a-x)\leq n/2 \\0 & \text{ otherwise } \end{cases}$$
</p>

<p style="text-align: justify;">
  Where wt is the weight of a bit-string (number of 1).
</p>

<p style="text-align: justify;">
  Alternatively we can write : $$ m_a(x) = \Theta (n/2 &#8211; wt(x-a) )$$.
</p>

<p style="text-align: justify;">
  The problem is : <strong>determine a</strong> given an access to answers from $$m_a$$.
</p>

<p style="text-align: justify;">
  We saw in the presentation (link available soon) that the classical complexity was $$ O(n)$$ while the quantum complexity was $$ O(\sqrt{n})$$. In the following we show the classical bound.
</p>

<p style="text-align: justify;">
  <h2 style="text-align: justify;">
    The classical algorithm
  </h2>
  
  <p>
    For the classical case we will use a dichotomic process as in the <a href="http://en.wikipedia.org/wiki/Binary_search_algorithm" target="_blank">binary chop</a>. Here is the algorithm :
  </p>
  
  <ul>
    <li>
      At the first step you look the result for 0&#8230;0. If it&#8217;s 1 you take all the possible weights that could have the same result ($$2^n / 2 = 2^{n-1}$$ weights possible). If it&#8217;s 0 you take the complementary set of bits (the same number of weights if n is even).
    </li>
    <li>
      After that, you choose a new vector in your possible set, with the biggest Hamming distance with the previous tested bit. Then you look the result. After that step you would be able to remove another time : $$ 2^{n-1} / 2$$ remaining weights .
    </li>
    <li>
      &#8230; you repeat these steps n-1 times at all, in the end you have $$2^n/2^{n-1} = 2$$ possible states.
    </li>
    <li>
      In the end, you may have two bits that you will separate by choosing a special bit <strong>b</strong>.  This bit <strong>b</strong> will depend on the two possible states and differentiate them.
    </li>
    <li>
      And you are done in n steps.
    </li>
  </ul>
  
  <h2>
    Example for n=3
  </h2>
  
  <p>
    For n=3, let&#8217;s take the example of the following target bit : w = 001.
  </p>
  
  <ul>
    <li>
      I first try 000. I get 1. So the possible weights are : 000 / 001 / 010 / 100
    </li>
    <li>
      Then I test 001. I get 1. So the remaining states are 001 / 000 ( 011 / 101 are not possible because they are not in the previous set)
    </li>
    <li>
      Finally I test 101. I get 1. <em>So the only possible result is 001</em>.
    </li>
  </ul>