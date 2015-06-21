---
title: Decomposition in unitary matrices
author: Jice

date: 2009-07-07
url: /2009/07/decomposition-in-unitary-matrices/
categories:
  - Maths
tags:
  - Linear Algebra
---
**Conjecture** : Any complex or real matrix is the sum of two unitary matrices.

**Proof** (ideas) :

We know that every complex matrix A could be diagonalized using two unitary matrices U and V : $$ A = UDV^{*} $$ . The matrix D has positive elements : D=diag(d1,&#8230;d2) with  $$d\_1\geq d\_2 \geq &#8230;\geq d_n \geq 0$$.

**A basic result is the following** : every diagonal matrix could be diagonalized with n unitary matrix. Indeed,  you just have to choose the good coefficient and use the set of matrix {$$ E\_i $$} where $$E\_i$$ is a diagonal with -1 everywhere, except at position i  where there is a +1:

<p style="text-align: center;">
  $$\begin{pmatrix} -1 & & & & & & & & \\ & & \ddots & & & & 0 & & \\ & & & -1 & & & & & \\ & & & & 1 & & & & \\ & & 0 & & & -1 & & & \\ & & & & & & \ddots & & \\ & & & & & & & 1 & \end{pmatrix}$$
</p>

The matrices in this set are unitary, and they are a basis of diagonal matrices.

**Result for a sum of only two terms :**

For n=2 we see that the previous matrices (Ei)  works, and there are only two of them.

For any n, I think that we could prove the hypothesis : Every diagonal matrix could be a sum of two block matrix as the following :

<p style="text-align: center;">
  $$\begin{pmatrix}<br /> (U) & & 0\\<br /> & & \\<br /> 0& & 1<br /> \end{pmatrix}<br /> ,<br /> \begin{pmatrix}<br /> 1& & 0 \\<br /> & & \\<br /> 0 & & (V)<br /> \end{pmatrix}$$
</p>

<p style="text-align: justify;">
  I have not the end of the proof, but I was thinking of writing D as the sum or product of matrix of the form diag(1,d2,&#8230;dn+1) and diag(d1,d2,&#8230;dm,1). And applying a recurrence hypothesis, but I did not suceed.
</p>