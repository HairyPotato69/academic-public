---
title: Solving Recurrences
draft: false
tags:
  - DSA
  - Notes
  - Algorithm-Analysis
description:
---
>[!WARNING] Recursion
>See this first: [[Recursion]]
# Expansion Method
As the name suggests, this method simply expands the function repeatedly and recursively. This can be confusing at times but, you'll get used to it. 

Prove $T(n) = 4T(\frac{n}{2}) + n^3$, prove $T(n)=O(n^3)$.
$$
\begin{align}
T(n) &= 4T(\frac{n}{2}) + n^3 \\
& = 4[4T(\frac{n}{2^2}) + (\frac{n}{2})^3] + n^3 \\
& = 4^2T(\frac{n}{2^2}) + 4(\frac{n^3}{2^3}) + n^3 \\
& = 4^2T(\frac{n}{2^2}) + (\frac{n^3}{2}) + n^3 \\
& = 4^2[4T(\frac{n}{2^3}) + (\frac{n}{2^2})^3] + (\frac{n^3}{2}) + n^3 \\
& = 4^3T(\frac{n}{2^3}) + (\frac{n^3}{2^6}) + (\frac{n^3}{2}) + n^3 \\
& = 4^3T(\frac{n}{2^3}) + (\frac{n^3}{2^2}) + (\frac{n^3}{2}) + n^3 \\
& = 4^3T(\frac{n}{2^3}) + n^3[(\frac{1}{2^2}) + (\frac{1}{2}) + 1] \\
\end{align} 
$$
Progression until the third iteration usually suffices. 

*So, now what?*

In this line, $4^3T(\frac{n}{2^3}) + n^3[(\frac{1}{2^2}) + (\frac{1}{2}) + 1]$, the $(\frac{1}{2^2}) + (\frac{1}{2}) + 1$ is a geometric progression. The geometric progression can be simplified to this $1 + (\frac{1}{2}) + (\frac{1}{2^2}) + (\frac{1}{2^3})+...+(\frac{1}{2^{k-1}})$

The summation formula for a GP is $\frac{a(r^n-1)}{r-1}$ or $\frac{a(1-r^n)}{1-r}$. Notice that in each progression, the denominator is becoming larger and larger while the nominator is still one. This means that as the recursion goes on, the values will diminish to 0 or very near 0.

So,
$$
\begin{align}
\Sigma G(n) &= \frac{a(1-r^n)}{1-r} \\
&= \frac{1(1-\frac{1}{2}^{k-1})}{1-\frac{1}{2}} \\
&=2(1-(\frac{1}{2})^{k-1})\\
&=2(1-(\frac{1^{k-1}}{2^{k-1}}))\\
&< 2(1-0)\\
&=2
\end{align}
$$
Since, you're approximating, there will be loss of value. 

The statements in-front can also be simplified,
$$
\begin{align}
&= 4^3T(\frac{n}{2^3})\\
& = 4^kT(\frac{n}{2^k})
\end{align}
$$

Then, eventually, the recursion will come to an end, $T(1)$.
$$
\begin{align}
\text{let } \frac{n}{2^k} = 1 \\
n = 2^k \\
\log n = k \log2 \\
\log n = k \text{ or } k = \log n
\end{align}
$$
So, the final answer is,
$$
\begin{align}
T(n) &= 4T(\frac{n}{2}) + n^3 \\
& = 4[4T(\frac{n}{2^2}) + (\frac{n}{2})^3] + n^3 \\
& = 4^2T(\frac{n}{2^2}) + 4(\frac{n^3}{2^3}) + n^3 \\
& = 4^2T(\frac{n}{2^2}) + (\frac{n^3}{2}) + n^3 \\
& = 4^2[4T(\frac{n}{2^3}) + (\frac{n}{2^2})^3] + (\frac{n^3}{2}) + n^3 \\
& = 4^3T(\frac{n}{2^3}) + (\frac{n^3}{2^6}) + (\frac{n^3}{2}) + n^3 \\
& = 4^3T(\frac{n}{2^3}) + (\frac{n^3}{2^2}) + (\frac{n^3}{2}) + n^3 \\
& = 4^3T(\frac{n}{2^3}) + n^3[(\frac{1}{2^2}) + (\frac{1}{2}) + 1] \\
& < 4^kT(\frac{n}{2^k}) + n^3(2) \\
& = n^2T(1) + 2n^3 \\
& = n^2 + 2n^3 \\
& = O(n^3)
\end{align} 
$$

>[!Practice]
>Use this to get a quick solution for an easy problem 
# Mathematical Induction/Substitution Method

# ⭐Master Method 