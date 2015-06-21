---
title: Impatient Learning and sub/sup Majority Problem
author: Jice

date: 2009-09-16
url: /2009/09/impatient-learning-and-subsup-majority-problem/
categories:
  - Quantum Learning
---
<p style="text-align: justify;">
  In this article I present some probabilities of 1-step learning optimized by Impatient Learning (<a href="http://www.citebase.org/abstract?id=oai:arXiv.org:quant-ph/0309059" target="_blank">http://www.citebase.org/abstract?id=oai:arXiv.org:quant-ph/0309059</a>) for the sub/sup Majority Learning.
</p>

<h2 style="text-align: justify;">
  The (Sub/Sup) Majority Learning
</h2>

<p style="text-align: justify;">
  Take a bitstring <em>a</em>, and an integer $$\theta$$. The oracle will respond 0 if $$d(a,x)\leq \theta$$  if queried with <em>x</em> and 1 otherwise. In other terms this oracle reply yes if two bitstrings agree on at least $$\theta$$ bit.
</p>

<p style="text-align: justify;">
  Here are the probability with a simple membership oracle (used with the usual phase kickback trick). Only even <em>n</em> gives an invertible matrix for the use of impatient learning.
</p>

<table style="width: 100%;" border="0" align="center">
  <tr style="text-align: center;">
    <td>
      n \ theta
    </td>
    
    <td>
    </td>
    
    <td>
      1
    </td>
    
    <td>
      2
    </td>
    
    <td>
      3
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr style="text-align: center;">
    <td>
      2
    </td>
    
    <td style="text-align: center;">
      1
    </td>
    
    <td style="text-align: center;">
      <strong>1</strong>
    </td>
    
    <td style="text-align: center;">
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
  </tr>
  
  <tr style="text-align: center;">
    <td style="text-align: center;">
      4
    </td>
    
    <td style="text-align: center;">
      0.6875
    </td>
    
    <td>
      0.875
    </td>
    
    <td>
      <strong>0.875</strong>
    </td>
    
    <td>
      0.6875
    </td>
    
    <td>
      X
    </td>
  </tr>
  
  <tr style="text-align: center;">
    <td>
      6
    </td>
    
    <td>
      0.3671875
    </td>
    
    <td>
      0.6171875
    </td>
    
    <td>
      0.75
    </td>
    
    <td>
      <strong>0.75</strong>
    </td>
    
    <td>
      0.6171875
    </td>
  </tr>
  
  <tr style="text-align: center;">
    <td>
      8
    </td>
    
    <td>
      0.1865234
    </td>
    
    <td>
      0.36132812
    </td>
    
    <td>
      0.520508
    </td>
    
    <td>
      0.6484
    </td>
    
    <td>
      <strong>0.6484</strong>
    </td>
  </tr>
  
  <tr style="text-align: center;">
    <td>
      10
    </td>
    
    <td>
      0.0936279
    </td>
    
    <td>
      0.1990967
    </td>
    
    <td>
      0.312499
    </td>
    
    <td>
      0.448241
    </td>
    
    <td>
      0.5703125
    </td>
  </tr>
</table>

<p style="text-align: justify;">
  <p style="text-align: justify;">
    <p style="text-align: justify;">
      For all these value, the optimum is achieved when the phase kickback takes value in {-1 ; 1}.
    </p>
    
    <p>
      <br class="_mce_marker" />
    </p>