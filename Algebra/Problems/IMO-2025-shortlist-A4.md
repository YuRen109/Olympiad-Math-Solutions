# <span id="problem"></span>Problem
Let $\text{ℤ}\_{\geq 0}$ be the set of all nonnegative integers.  
Let $f: \text{ℤ}\_{\geq 0} \to \text{ℤ}\_{\geq 0}$ be an unbounded function such that, 
if $m$ and $n$ are nonnegative integers satisfying  

$$f(m+n) =  \max \lbrace f(0), f(1), \cdots, f(m+n)\rbrace,$$

then 

$$f(m+n) = f(m) + f(n).$$

Prove that there exist positive integers $A$, $B$, $C$ and $D$ such that 
for all nonnegative integers $n$,  

$$f(An + B) = Cn + D.$$  

We say that $f$ is *unbounded* if for each nonnegative integer $N$, there exists some nonnegative integer $n$ such that $f(n) \geq N$.

# Source

[IMO 2025 Problems](https://www.imo-official.org/problems/2025/)

# Key Idea
1. It suffices to pick some **representative nonnegative integers** to show
   the property of $f$, that is being proven, says that $f$ maps an arithmetic progression to another one,
   and further preserves its order, if our selection process is relevant to $\max$.  
2. By the unboundedness of $f$, if we determine its function values from small integers to large ones,
   we always get one whose function value is greater those of the determined small integers.
   Then we pick it and call it **a representative nonnegative integer**.
3. After picking all representative integers, 
   we may think about **the function values of the points inside each gap between adjacent representatives**.  
   It is not hard to find out that these values have a pattern similar to a previous segment. This is because of the additivity of $f$.  
   This is because of the additivity of $f$, and also, this is where we see an arithmetic progression comes.  
4. We start to study **the gap lengths between adjacent representatives**.  
   
5. Finally, we may find **the gap lengths keep constant** for sufficiently large adjacent representatives.
   Therefore, we complete the proof.

# Solution


Let 

$$\text{ℳ} = \lbrace k \in \text{ℤ}\_{\geq 0} \mid f(k) = \max \lbrace f(0), f(1), \cdots, f(k)\rbrace \rbrace.$$

### <span id="claim1"></span>Claim 1 ($f(0) = 0$ and $f(1) > 0$)
$f(0) = 0$ and $f(1) > 0$.

*Proof.*  
It is apparent that $0 \in \text{ℳ}$.  
Plugging $m=n=0$ into $f(m+n) = f(m) + f(n)$ we get $f(0+0) = f(0) + f(0)$, or $f(0) = 0$.  

Consider the set $\lbrace n \in  \text{ℕ} \mid f(n) > 0 \rbrace$, which is non-empty because of the unboundedness of $f$.  

Let $k \in \text{ℕ}$ be the smallest number of $\lbrace n \in  \text{ℕ} \mid f(n) > 0 \rbrace$.  
Then $k \in \text{ℳ}$.  

If $k=1$, then we complete the proof.  

Suppose that $k \geq 2$. Then 

$$f(1) = f(2) = \cdots = f(k-1) = 0.$$

However, $0 < f(k) = f(1) + f(k-1) = 0 + 0 = 0$, a contradiction.  

$\square$  

<span id="def_ai"></span>Inspired by [Claim 1](#claim1), construct a sequence $a_0, a_1, \cdots$ as follows.  

1. Define $a_0 = 1$.
2. For each $i \in \text{ℕ}$ we define $a_i$ to be the smallest number of $\lbrace n \in  \text{ℕ} \mid n > f(a_{i-1}) \rbrace$.  
   Note that such an $a_i$ exists because of the unboundedness of $f$ for each $i \in \text{ℕ}$. 

Then $a_i \in \text{ℳ}$ and $a_i < a_{i+1}$ for each $i \in \text{ℤ}\_{\geq 0}$.  
Therefore, we have the following propery:

$$f(a_i) = f(n) + f(a_i - n)$$

for each $i \in \text{ℤ}\_{\geq 0}$ and each nonnegative integer $n \leq a_i$.  

Using this property, we may derive the following claim.

### <span id="claim2"></span>Claim 2 (the value of $f(k)$ for each integer $k$ inside the gaps of $a_n$)
For each $i \in \text{ℤ}\_{\geq 0}$ and each $k \in \text{ℕ}$,  
if 

$$a_i < k < a_{i+1},$$

then

$$0 \< f(k) \< f(a_i).$$

*Proof.*  
Let $k \in \text{ℕ}$ with $a_i < k < a_{i+1}$.  
Then by [the definition](#def_ai) of $a_n$ we get $0 \leq f(k) \leq f(a_i)$.  

Suppose that $f(k) = 0$.  
Then $f(a_{i+1}) = f(a_{i+1} - k) + 0 > f(a_i)$.  
However, $a_{i+1} - k < a_{i+1}$, a contradiction to [the definition](#def_ai) of $a_n$.  

Suppose that $f(k) = f(a_i)$.  
Then $k \in \text{ℳ}$ since, 
otherwise, we would get some $k^\prime \in \text{ℕ}$ such that 
$a_i < k^\prime < k < a_{i+1}$ but $f(k^\prime) > f(k) = f(a_i)$.  
Therefore, $f(k) = f(a_{i}) + f(k - a_{i})$, or $f(k - a_{i}) = 0$.  
Since $0 < k - a_{i} < a_{i+1}$,  

$$ f(a_{i}) < f(a_{i+1}) = f(a_{i+1} - k + a_i) + f(k - a_{i}) = f(a_{i+1} - k + a_i) $$

However, $a_{i+1} - k + a_i < a_{i+1}$, a contradiction to [the definition](#def_ai) of $a_n$.


$\square$  


We will look into the distribution of $a_0, a_1, \cdots$ with [Claim 2](#claim2).  


### <span id="claim3"></span>Claim 3 (the gap lengths of $a_n$ cannot shrink)
For each $i \in \text{ℕ}$ we have

3.1 $a_{i+1} -a_i \geq a_i -a_{i-1}$, and  
3.2 $f(a_{i+1}) - f(a_i) \leq f(a_i) - f(a_{i-1})$

*Proof.*  
First, we will prove Claim 3.1.  
Suppose that $a_{j+1} -a_j < a_j -a_{j-1}$ for some $j \in \text{ℕ}$.  
Then 

$$a_{j-1} < a_{j+1} - a_{j} + a_{j-1} < a_{j}.$$

By [Claim 2](#claim2) we have $f(a_{j+1} - a_{j} + a_{j-1}) < f(a_{j-1})$.  
However, 

$$
\begin{aligned}
f(a_{j+1}) &= f(a_{j+1} - a_{j} + a_{j-1}) + f(a_j - a_{j-1}) \\
&= f(a_{j+1} - a_{j} + a_{j-1}) + f(a_j) - f(a_{j-1}) \\
&< f(a_{j-1}) + f(a_j) - f(a_{j-1}) = f(a_j),
\end{aligned}
$$

a contradiction to [the definition](#def_ai) of $a_n$. 

Hence, Claim 3.1 holds.  

Claim 3.2 is a corollary of Claim 3.1:  

By Claim 3.1 we have $a_{i+1} > a_{i+1} - a_i + a_{i-1} \geq a_i$ for each $i \in \text{ℕ}$.  
By [Claim 2](#claim2) we have  

$$f(a_{i+1}) - f(a_i) + f(a_{i-1}) = f(a_{i+1} - a_i + a_{i-1}) \leq f(a_i),$$

or $f(a_{i+1}) - f(a_i) \leq f(a_{i}) - f(a_{i-1})$.

$\square$  



### <span id="claim4"></span>Claim 4 (the gap lengths of $a_n$ are finally fixed)
There exists $l \in \text{ℕ}$ such that 
for each $i \in \text{ℕ}$ with $i > l$ we have $a_{i+1} -a_i = a_i -a_{i+1}$.

*Proof.*  

Suppose that for every $l \in \text{ℕ}$ there is some $n \in \text{ℕ}$ with $n > l$ 
such that $a_{n+1} - a_n > a_n - a_{n-1}$.  

Construct a sequence $n_0,n_1,\cdots$ as follows.  
1. Define $n_0=1$.
2. For each $i \in \text{ℕ}$ find $n_i \in \text{ℕ}$ such that $n_{i} > n_{i-1}$ and $a_{n_{i} + 1} - a_{n_i} > a_{n_i} - a_{n_{i} - 1}$.  

Then by [Claim 3.1](#claim3) we have 

$$a_{n_i} - a_{n_i - 1} < a_{n_i + 1} - a_{n_i} \leq a_{n_{i + 1}} - a_{n_{i+1} - 1}$$

and by [Claim 3.2](#claim3) we have 

$$f(a_{n_i}) - f(a_{n_i -1}) > f(a_{n_{i+1}}) - f(a_{n_i})$$

for all $i \in \text{ℕ}$.

However, this implies that there is some $i^\star \in \text{ℕ}$ such that 

$$f(a_{n_{1}}) - f(a_{n_{0}}) > f(a_{n_{2}}) - f(a_{n_{1}}) > \cdots > 0 > f(a_{n_{i^\star + 1}}) - f(a_{n_{i^\star}}) > \cdots,$$  

or $f(a_{n_{i^\star + 1}}) < f(a_{n_{i^\star}})$, a contradiction. 

Hence, there exists $l \in \text{ℕ}$ such that 
for each $i \in \text{ℕ}$ with $i > l$ we have  

$$a_{i+1} -a_i \leq a_i -a_{i+1},$$ 

and, furthermore, $a_{i+1} -a_i = a_i -a_{i+1}$ by [Claim 3.1](#claim3).

$\square$  


By [Claim 4](#claim4) we may find $l \in \text{ℕ}$ such that 

$$a_{l+1} - a_{l} = a_{l+2} - a_{l+1} = \cdots,$$

or $a_{l+x} = a_l + x (a_{l+1} - a_{l})$ for all $x \in \text{ℤ}\_{\geq 0}$.

And we also have 

$$ f(a_{l+1}) - f(a_{l}) = f(a_{l+2}) - f(a_{l+1}) = \cdots,$$

or $f(a_{l+x}) = f(a_l) + x \left[ f(a_{l+1}) - f(a_{l}) \right]$.

Let

$$
\begin{aligned}
A &= a_{l+1} - a_l &\in \text{ℕ}, \\
B &= a_l &\in \text{ℕ}, \\
C &= f(a_{l+1}) - f(a_l) &\in \text{ℕ}, \\
D &= f(a_l) &\in \text{ℕ}.
\end{aligned}
$$

Then 

$$f(Ax + B) = f(a_l + x(a_{l+1} - a_l)) = f(a_{l+x}) = f(a_l) + x \left[ f(a_{l+1}) - f(a_{l}) \right] = C + Dx$$

for all $x \in \text{ℤ}\_{\geq 0}$.

# What I Learned

This is a constructive proof that was figured out by depicting graphs and reasoning on them.  

I got the conclusion in a visualized way at first, and then derived it in logic languages.
