# <span id="problem"></span>Problem

Let $S$ be a set of positive integers, possibly infinite, such that no positive integer greater than 1 divides all elements of $S$.  
Determine all non-periodic infinite sequences $a_1, a_2, \cdots$ of positive integers such that, for all positive integers $n$,  
1. $a_n \leq \left| a_{n+l} - l \right|$ for all $l \in S$, and
2. $a_n = \left| a_{n+l} - l \right|$ for at least one $l \in S$.  


We say that an infinite sequence $a_1, a_2, \cdots$ is *periodic* if there exists a positive integer $t$ such that $a_n = a_{n+t}$ for all positive integers $n$.  

# Source

[IMO 2025 Problems](https://www.imo-official.org/problems/2025/)

# Key Idea

1. Look into properties of $S$.  
   Consider some tricks related to $\text{gcd}$ (for example, [Bézout's identity](https://en.wikipedia.org/wiki/B%C3%A9zout%27s_identity))
   because of the property that **"no positive integer greater than 1 divides all elements of $S$"**.     
2. Find **finitely many key elements** in $S$ (even though it is infinite) and use them to see properties of $a_n$,
   because finitely many key elements are sufficient to represent properties of $S$ where $a_n$ would be confined, 
   if the properties are relevant to $\text{gcd}$.  
   Besides, avoid defining $\text{gcd}$ for infinite sets of integers.  
4. Observe **the condition 2** and the requirement of **non-periodic infinite sequences** in [the problem statement](#problem).  
   Imagine that $a_n$ would finally escape from periodicity as $n$ goes to infinity.  
   Should be incline to that **$a_n$ is unbounded**.
5. Get that $a_n$ increases to the end once it starts to increase (and it eventually does).  
   Analyze **the increasingness of $a_n$ for large $n$**.
6. Get the increasingness of $a_n$ from **the conditions 1 and 2 and those key elements**.  
   Realize that **those key elements determine finite probable steps of $a_n$ for large $n$**.  
7. Realize that with those probable steps one can determine $a_n$ for all large enough $n$ 
   thanks to that the greatest common divisor of those key elements is 1.  
   Get the form of the solution for all large enough $n$.  
8. Argue the uniqueness of the form for all $n$.  

# Solution

Let $\text{𝕊}$ denote the collection of all subsets $S$ of $\text{ℕ}$ such that no positive integer greater than 1 divides all elements of $S$.  
For any finite non-empty subset $T$ of $\text{ℕ}$, let $\text{gcd }T$ denote the greatest common divisor of all elements of $T$.  
For any finite subset $F$ of $\text{ℕ}$, let ${\\#} F$ denote the number of elements of $F$.  

Then we have the following result.
### <span id="claim1"></span>Claim 1 (a property of $S$)
For any non-empty $S \in \text{𝕊}$ there exists a finite non-empty subset $S^\prime$ of $S$ such that $\text{gcd } S^\prime = 1$.  

*Proof.*   
For the case where $S$ is finite, we have that $\text{gcd }S = 1$ because, otherwise, 
$\text{gcd }S > 1$ would be a positive integer that divides all elements of $S$.  
In this case we may find $S^\prime = S$.  

For the case where $S$ is infinite, suppose that every finite subset $S^\prime$ of $S$ satisfies that $\text{gcd }S^\prime > 1$.  
Construct an infinite sequence $s_1, s_2, \cdots$ of elements of $S$ such that  
1. $s_1$ is the smallest number in $S$, and 
2. $s_n$ is the smallest number in $S \backslash \lbrace s_1, s_2, \cdots, s_{n-1} \rbrace$ for each $n \in \text{ℕ}$.  

The above process is ordering the elements of $S$.  
For any $n \in \text{ℕ}$ we denote $S_n = \lbrace s_1, s_2, \cdots, s_n \rbrace$.  
Then we have that $\text{gcd }S_n > 1$ for all $n \in \text{ℕ}$, and 

$$ s_1 = \text{gcd }S_1 \geq \text{gcd }S_2 \geq \cdots , $$

which implies that for all sufficiently large $n$ we have $\text{gcd }S_n = d$, where $d \in \text{ℕ}$.  
However, $d > 1$ and, by induction, we get that $d$ divides all elements of $S$, a contradiction.  

$\square$

Suppose that there is some $S \in \text{𝕊}$ such that such a non-periodic sequence $a_1, a_2, \cdots$ of positive integer, 
which may be dependent of $S$, in [the problem statement](#problem) exist.  
In this case, let $S^\star \subseteq S$ denote the collection of each $s^\star \in S$ 
such that $a_n = \left| a_{n+s^\star} - s^\star \right|$ for all $n \in \text{ℕ}$.  
The condition 2 in [the problem statement](#problem) implies that $S^\star$ is non-empty, and therefore, $S$ is non-empty.  

For any $s \in S$ and for any $s^\star \in S^\star$ we denote  

$$
\begin{aligned}
\text{𝒜}(s) &= \lbrace n \in \text{ℕ} \mid a_{n+s} \geq s + a_n \rbrace, \\
\text{ℬ}(s) &= \lbrace n \in \text{ℕ} \mid a_{n+s} \leq s - a_n \rbrace = \text{ℕ} \backslash \text{𝒜}\left( s \right), \\
\text{𝒜}^{\star}(s^\star) &= \lbrace n \in \text{ℕ} \mid a_{n+s^\star} = s^\star + a_n \rbrace , \\
\text{ℬ}^{\star}(s^\star) &= \lbrace n \in \text{ℕ} \mid a_{n+s^\star} = s^\star - a_n \rbrace = \text{ℕ} \backslash \text{𝒜}^{\star}\left( s^\star \right).
\end{aligned}
$$

Then, as stated in [the problem](#problem), we have that  

$$ \left[ n \in \text{𝒜}(s) \iff n \notin \text{ℬ}(s) \right] \text{  and  } \left[ n \in \text{𝒜}^{\star}(s^\star) \iff n \notin \text{ℬ}^{\star}(s^\star) \right] $$

for any $s \in S$, any $s^\star \in S^\star$ and any $n \in \text{ℕ}$.  

Furthermore, we have the following results.  

### <span id="claim2"></span>Claim 2 (properties of $\text{𝒜}(s)$ and $\text{𝒜}^\star {(s^\star)}$)  
Let $s \in S$, $s^\star \in S^\star$ and $k \in \text{ℕ}$. Then  
2.1    $k \in \text{𝒜}(s) \iff \left[ a_{k} > s \text{  or  } a_{k+s} > s \right]$.  
2.2    $k \in \text{𝒜}^{\star}(s^\star) \iff \left[ a_{k} > s^\star \text{  or  } a_{k+s^\star} > s^\star \right]$.  
2.3    If $k \in \text{𝒜}(s)$, then $k + ns \in \text{𝒜}$ for all $n \in \text{ℕ}$.  
2.4    If $k \in \text{𝒜}^{\star}(s^\star)$, then $k + ns \in \text{𝒜}^\star$ for all $n \in \text{ℕ}$.  

*Proof.*  
First, we will prove Claim 2.1.  
Claim 2.1 holds since 

$$k \in \text{𝒜}(s) \iff a_{k+s} \geq s + a_{k} > s \implies \left[ a_{k} > s \text{  or  } a_{k+s} > s \right], $$

and  

$$ k \in \text{ℬ}(s) \iff a_{k+s} \leq s - a_{k} \implies \left[ a_{s} \leq s \text{  and } a_{k+s} \leq s \right]. $$

In a similar way we can prove Claim 2.2.  

Next, we will prove Claim 2.3.  
$k \in \text{𝒜}$ implies that $a_{k+s} \geq s + a_{k} > s$.  
Suppose $k+s \in \text{ℬ}$. Then $a_{k+2s} \leq s - a_{k+s}$, which implies that  

$$ a_{k+s} \leq s - a_{k+2s} < s, $$

a contradiction. Hence, $k+s \in \text{𝒜}$. By induction we complete the proof of Claim 2.3.  
In a similar way we can prove Claim 2.4.  
$\square$

We may always find a finite non-empty subset $S^\prime$ of $S$ such that $\text{gcd }S^\prime = 1$ and $S^\prime \cap S^\star \neq \emptyset$ by the following process: 
1. Find a finite non-empty subset $S^{\prime\prime}$ of $S$ such that $\text{gcd }S^{\prime\prime} = 1$ by [Claim 1](#claim1).  
2. Find an element $s^\star \in S^\star$ since $S^\star$ is non-empty.  
3. Let $S^{\prime} = \lbrace s^\star \rbrace \cup S^{\prime\prime}$.  

Such a $S^{\prime}$ may be written as $S^\prime = \lbrace s_1, s_2, \cdots, s_{{\\#} S^\prime} \rbrace$ 
where $s_1 \in S^\star$ and $s_1, s_2, \cdots, s_{{\\#} S^\prime} \in S$.  
Denote $\text{𝒜}_i = \text{𝒜}(s_i)$ and $\text{ℬ}_i = \text{ℬ}(s_i)$ for each $i \in \lbrace 1, 2, \cdots, {\\#} S^\prime\rbrace$ 
and, especially $\text{𝒜}^{\star}_1 = \text{𝒜}^{\star}(s_1)$ and $\text{ℬ}^{\star}_1 = \text{ℬ}^{\star}(s_1)$.  

The result of the trivial case where ${\\#} S^\prime = 1$ is shown as follows.  

### <span id="claim3"></span>Claim 3 (the trivial case where ${\\#} S^\prime = 1$)

3.1 ${\\#} S^\prime = 1$ if and only if $S^\prime = \lbrace 1 \rbrace$.  
3.2 If ${\\#} S^\prime = 1$, then $a_{n+1} = a_n + 1$ for all $n \in \text{ℕ}$ (with $a_1 \in \text{ℕ}$).  

*Proof.*  
It is apparent that Claim 3.1 holds.  
Now we will prove Claim 3.2.  
Since $1 \in S^\star$, for all $n \in \text{ℕ}$ we have $n \in \text{𝒜}^{\star}(1) \iff n \notin \text{ℬ}^{\star}(1)$, or  

$$ a_{n+1} = a_n + 1 \iff a_{n+1} \neq 1 - a_n .$$

Suppose $a_{k+1} = 1 - a_k$ for some $k \in \text{ℕ}$. Then $a_{k+1} + a_k = 1$, which is a contradiction 
since $a_k \geq 1$ and $a_{k+1} \geq 1$.  
Hence, $a_{n+1} = a_n + 1$ for all $n \in \text{ℕ}$.  
Since $a_n \in \text{ℕ}$ for all $n \in \text{ℕ}$, it is necessary to let $a_1 \in \text{ℕ}$.  

It is apparent that a sequence with $a_{n+1} = a_n + 1$ for all $n \in \text{ℕ}$ 
satisfies the conditions 1 and 2 in [the problem statement](#problem).

$\square$

Before jumping into the discussion of general cases where ${\\#} S^\prime > 1$, we state some useful theorems here.  

### <span id="bezout"></span>Theorem 4 ([Bézout's identity](https://en.wikipedia.org/wiki/B%C3%A9zout%27s_identity))
Let $N = \lbrace n_1, n_2, \cdots, n_k \rbrace$ be a set of $k$ positive integers with $\text{gcd }N = 1$.  
Then there exist $x_1, x_2, \cdots, x_k \in \text{ℤ}$ 
such that 

$$x_1 n_1 + x_2 n_2 + \cdots + x_k n_k = 1.$$

### <span id="num_semi"></span>Theorem 5 (a corollary from a fundamental theorem of [Numerical semigroups](https://en.wikipedia.org/wiki/Numerical_semigroup))
Let $N = \lbrace n_1, n_2, \cdots, n_k \rbrace$ be a set of $k$ positive integers with $\text{gcd }N = 1$.  
Then for all sufficiently large $m \in \text{ℕ}$ there exist $x_1, x_2, \cdots, x_k \in \text{ℕ}$ 
such that 

$$x_1 n_1 + x_2 n_2 + \cdots + x_k n_k = m.$$

*Proof.*  
This a simple corollary from a fundamental theorem of [Numerical semigroups](https://en.wikipedia.org/wiki/Numerical_semigroup).  
Here we provide a proof without the need of introducing the concept of Numerical semigroups.  

Suppose $k = 1$. Then $\text{gcd }N = 1$ implies that $N = \lbrace 1 \rbrace$, 
and for all $m \in \text{ℕ}$ we may find $x_1 = m$ such that $x_1 \cdot 1 = m$.  
Suppose $k > 1$. It suffices to show that for each $r \in \lbrace 1, 2, \cdots, n_1 - 1 \rbrace$ 
there exist $x_2, x_3, \cdots, x_k \in \text{ℕ}$ such that 

$$\sum^{k}_{i=2} x_i n_i \equiv r \pmod{n_1}.$$

By [Bézout's identity](#bezout), since $\text{gcd }N = 1$, 
we may find $z_1, z_2, \cdots, z_k \in \text{ℤ}$ such that $\sum^{k}_{i=1} z_i n_i = 1$, or  

Let $r \in \lbrace 1, 2, \cdots, n_1 - 1 \rbrace$.  

Then 

$$\sum^{k}_{i=2} (r z_i) n_i \equiv r \pmod{n_1}.$$

Note that for all $t_{r,2}, t_{r,3}, \cdots, t_{r,k} \in \text{ℤ}$ we have

$$\sum^{k}_{i=2} (r z_i + t_{r,i} n_1) n_i \equiv r \pmod{n_1}.$$

For each $r \in \lbrace 1, 2, \cdots, n_1 - 1 \rbrace$ and 
for each $i \in \lbrace 2, 3, \cdots, k-1 \rbrace$ 
we may pick a sufficiently large $t_{r,i}$ such that $x_i = r z_i + t_{r,i} n_1 > 0$.  
Then the proof is complete.  

$\square$


### <span id="claim6"></span>Claim 6 
For all sufficiently large $n \in \text{ℕ}$ we have 

$$n \in \text{𝒜}^\star\_1 \cap \text{𝒜}\_2 \cap \cdots \cap \text{𝒜}\_{{\\#}S^\prime} = \text{𝒜}^\star\_1 \cap \left( \bigcap_{i=2}^{{\\#}S^\prime} \text{𝒜}\_i \right).$$

*Proof.*  
We have that there is some $C \in \text{𝒜}^\star_1$ because, otherwise, we get $a_n$ with $a_{n+s_1} = s_1 - a_n$ for all $n \in \text{ℕ}$, 
which is periodic.  

For each $i \in \lbrace 1, 2, \cdots, {\\#}S^\prime-1\rbrace$ we pick $c_i \in \text{ℕ}$ with $c_i s_i > s_{i+1}$.  
Then by the following process we may show that 

$$C + \sum_{i=1}^{{\\#}S^\prime-1} (c_i + x_i) s_i + x_{{\\#}S^\prime} s_{{\\#}S^\prime} \in \text{𝒜}^\star_1 \cap \left( \bigcap_{i=2}^{{\\#}S^\prime} \text{𝒜}_i \right)$$ 

for all $x_1, x_2, \cdots, x_{{\\#}S^\prime} \in \text{ℕ}$:  

   1. By [Claim 2.4](#claim2) and the fact that $C \in \text{𝒜}^\star_1$ we have $C + ( c_{1} + x_{1} ) s_{1} \in \text{𝒜}^\star_{1}$, 
and $a_{C + (c_1+x_1) s_1} = a_C + (c_1+x_1) s_1 > c_1 s_1 > s_2$, which, by [Claim 2.2](#claim2), implies further that

$$ C + (c_1+x_1) s_1 \in \text{𝒜}_2.$$

   Hence, $C + (c_1+x_1) s_1 \in \text{𝒜}^\star_{1} \cap \text{𝒜}_2$.  

   2. Suppose that for some $j \in \lbrace 2, \cdots, {\\#}S^\prime\rbrace$ we have 

$$C + \sum_{i=1}^{j-1} (c_i + x_i) s_i \in \text{𝒜}^\star_{1} \cap \left( \bigcap_{i=2}^{j-1} \text{𝒜}_i \right).$$

   Then 

$$a_{C + \sum_{i=1}^{j-1} (c_i + x_i) s_i} = a_{C} + \sum_{i=1}^{j-1} (c_i + x_i) s_i > c_{j-1} s_{j-1} > s_{j}.$$

   Hence, $C + \sum_{i=1}^{j-1} (c_i + x_i) s_i \in \text{𝒜}_j$ by [Claim 2.1](#claim2).  
   By [Claim 2.1 and 2.3](#claim2) we have 
   
$$a_{C + \sum_{i=1}^{j} (c_i + x_i) s_i} = a_{C + \sum_{i=1}^{j-1} (c_i + x_i) s_i} + (c_j + x_j) s_j = a_{C} + \sum_{i=1}^{j} (c_i + x_i) s_i > \max \lbrace s_1, s_2, ..., s_j \rbrace.$$

   Therefore, $C + \sum_{i=1}^{j} (c_i + x_i) s_i \in \text{𝒜}^\star_{1} \cap \left( \bigcap_{i=2}^{j} \text{𝒜}_i \right)$.  

   3. As $j$ runs over $2, \cdots, {\\#}S^\prime$ we finally conclude that 

$$C + \sum_{i=1}^{{{\\#}S^\prime}-1} (c_i + x_i) s_i \in \text{𝒜}^\star_1 \cap \left( \bigcap_{i=2}^{{\\#}S^\prime} \text{𝒜}_i \right),$$

   and also,  

$$C + \left(\sum_{i=1}^{{\\#}S^\prime-1} c_i s_i\right) +  \left(\sum_{i=1}^{{\\#}S^\prime} x_i s_i\right) = C + \sum_{i=1}^{{\\#}S^\prime-1} (c_i + x_i) s_i + x_{{\\#}S^\prime} s_{{\\#}S^\prime} \in \text{𝒜}^\star_1 \cap \left( \bigcap_{i=2}^{{\\#}S^\prime} \text{𝒜}_i \right).$$


By [Theorem 5](#num_semi), since $\text{gcd }S^\prime = 1$, there is $L \in \text{ℕ}$ such that, 
for all $m \in \text{ℕ}$ with $m \geq L$, 
there exist $x_1, x_2, \cdots, x_{{\\#}S^\prime} \in \text{ℕ}$ such that  $m = \sum_{i=1}^{{{\\#}S^\prime}} x_i s_i$.  
Let $L^\prime = L + C + \sum_{i=1}^{k-1} c_i s_i \in \text{ℕ}$.  
Then for all $m^\prime \in \text{ℕ}$ with $m^\prime \geq L^\prime$ we have $m^\prime \in \text{𝒜}^\star_1 \cap \left( \bigcap_{i=2}^{{{\\#}S^\prime}} \text{𝒜}_i \right).$

$\square$

### <span id="claim7"></span>Claim 7
For all sufficiently large $n \in \text{ℕ}$ we have $a_{n+1} = a_n + 1$.

*Proof.*  
By [Claim 6](#claim6) we have that there is some $L \in \text{ℕ}$ such that 
for all $n \in \text{ℕ}$ with $n \geq L$ we have 
$n \in \text{𝒜}^\star_1 \cap \left( \bigcap_{i=2}^{{\\#}S^\prime} \text{𝒜}\_i \right)$.

Suppose there are some $n \in \text{ℕ}$ with $n \geq L$ and some $j \in \lbrace 2, 3, \cdots, {{\\#}S^\prime}\rbrace$ 
such that $a_{n + s_j} > a_n + s_j$. Then 

$$ a_n + s_1 s_j = a_{n + s_1 s_j} = a_{n + s_j s_1} > a_n + s_j s_1, $$

a contradiction. 
Hence, we have that $a_{n + s_j} = a_n + s_j$ for all $n \in \text{ℕ}$ with $n \geq L$ and all $j \in \lbrace 2, 3, \cdots, {\\#}S^\prime\rbrace$.

Again, by [Bézout's identity](#bezout), since $\text{gcd } S^\prime = 1$, 
there are some $z_1, z_2, \cdots, z_{{\\#}S^\prime} \in \text{ℤ}$ such that $\sum_{i=1}^{{\\#}S^\prime} z_i s_i = 1$. 

Now we sort the sequence $z_1 s_1, z_2 s_2, \cdots, z_{{\\#}S^\prime} s_{{\\#}S^\prime}$ by defining a bijection $\bar{z}$
from $\lbrace 1, 2, \cdots, {\\#}S^\prime\rbrace$ to $\lbrace z_1 s_1, z_2 s_2, \cdots, z_{{\\#}S^\prime} s_{{\\#}S^\prime}\rbrace$ such that 

$$ \bar{z} (1) \geq \bar{z} (2) \geq \cdots > 0 > \cdots \geq \bar{z} ({\\#}S^\prime).  $$

Then $\sum_{i=1}^{j} \bar{z} (i) > 0$ for each $j \in \lbrace 1, 2, \cdots, {\\#}S^\prime\rbrace$.  
The construction of $\bar{z}$ helps with the application of $a_{n + s_j} = a_n + s_j$ for sufficiently large $n$.  

Let $n \in \text{ℕ}$ with $n \geq L$.  
Then we have $L \leq n + \sum_{i=1}^{j} \bar{z} (i)$ for each $j \in \lbrace 1, 2, \cdots, {\\#}S^\prime\rbrace$ 
(that is, $n + \sum_{i=1}^{j} \bar{z} (i)$ are sufficiently large by our definition in the context).  
Therefore,  

$$
\begin{aligned}
a_{n+1} = a_{n + \sum_{i=1}^{{{\\#}S^\prime}} z_i s_i} = a_{n + \sum_{i=1}^{{{\\#}S^\prime}} \bar{z} (i)} &= a_{n + \sum_{i=1}^{k-1} \bar{z} (i)} + \bar{z} ({{\\#}S^\prime}) \\
&= a_{n + \sum_{i=1}^{{{\\#}S^\prime}-2} \bar{z} (i)} + \bar{z} ({{\\#}S^\prime}) + \bar{z} ({{\\#}S^\prime}-1) \\
&\vdots \\
&= a_{n} + \bar{z} ({{\\#}S^\prime}) + \bar{z} ({{\\#}S^\prime}-1) + \cdots + \bar{z} (1) = a_n + \sum_{i=1}^{{{\\#}S^\prime}} z_i s_i = a_n + 1.
\end{aligned}
$$

$\square$

### <span id="claim8"></span>Claim 8

$$\text{𝒜}^\star_1 \cap \left( \bigcap_{i=2}^{{\\#}S^\prime} \text{𝒜}_i \right) = \text{ℕ}.$$

*Proof.*  
By [Claim 6](#claim6) we know that if $\text{ℬ}^\star_1 \cup \left( \bigcup_{i=2}^{{\\#}S^\prime} \text{ℬ}\_i \right) = \text{ℕ} \backslash \left[ \text{𝒜}^\star\_1 \cap \left( \bigcap_{i=2}^{{{\\#}S^\prime}} \text{𝒜}\_i \right) \right]$ is non-empty, 
then $\text{ℬ}^\star_1 \cup \left( \bigcup_{i=2}^{{\\#}S^\prime} \text{ℬ}\_{i} \right)$ contains a largest number.  
Suppose that $m \in \text{ℕ}$ is the largest number in $\text{ℬ}^\star_1 \cup \left( \bigcup_{i=2}^{{\\#}S^\prime} \text{ℬ}{\_i} \right)$. 
Then we have that $m \in \text{ℬ}^\star_1$ or $m \in \text{ℬ}{\_j}$ for some $j \in \lbrace 2, 3, \cdots, {\\#}S^\prime\rbrace$.  

By [Claim 7](#claim7) we have that $m+1 \in \text{𝒜}^\star\_1 \cap \left( \bigcap_{i=2}^{{{\\#}S^\prime}} \text{𝒜}\_i \right)$, 
and $a_{l+1} = a_{l} + 1$ for each $l \in \text{ℕ}$ with $l \geq m + 1$.  

For the case where $m \in \text{ℬ}^\star\_1$, we have that $a_{m+s_1} = s_1 - a_m$.  
However we also get $a_{m+s_1} = a_{m+1} + s_1 - 1$, implying that $a_{m} + a_{m+1} = 1$, a contradiction. 
Hence, $m \notin \text{ℬ}^\star\_1$.  

In a similar way we may prove that $m \notin \text{ℬ}^\star\_j$ for all $j \in \lbrace 2, 3, \cdots, {\\#}S^\prime\rbrace$.

$\square$

### <span id="claim9">Claim 9
For all $n \in \text{ℕ}$ we have $a_{n+1} = a_n + 1$ for all $n \in \text{ℕ}$ (with $a_1 \in \text{ℕ}$).

*Proof.*  
By [Claim 7](#claim7) and [Claim 8](#claim8) the proof is complete.  

$\square$  

By [Claim 3](#claim3) and [Claim 9](#claim9) we conclude that 
the only possible solution is $a_{n+1} = a_n + 1$ (with $a_1 \in \text{ℕ}$), or  

$$a_n = n + c$$

where $c \in \text{ℕ}$, for all $n \in \text{ℕ}$.

# What I Learned
1. [Bézout's identity](https://en.wikipedia.org/wiki/B%C3%A9zout%27s_identity)
2. [Numerical semigroups](https://en.wikipedia.org/wiki/Numerical_semigroup)
3. Picking finitely many key elements from an infinite set.
4. Arguing propositions hold for large $n$ at first, and then arguing them all hold for all $n$.
