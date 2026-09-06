# <span id="problem"></span>Problem
Let denote the set of positive integers.  
A function $f:$ is said to be *bonza* if

$$ f(a) \text{  divides  } b^a - f(b)^{f(a)}$$

for all positive integers $a$ and $b$.  
Determine the smallest constant $c$ such that $f(n) \leq cn$ for any bonza function $f$ and any positive integer $n$.

# Source

[BMO2 1995 Problems](https://bmos.ukmt.org.uk/home/bmo2-1995.pdf)

# Key Idea

1. Fix the order of $a,b,c$ since this is a symmetric proposition.  
2. Find the boundary of $a$, the smallest number of $a,b,c$.  
3. For each possible $a$, find the boundary of $b$, the smaller number of $b,c$.  
4. For each possible $a,b$, calculate $c$ and see if it is a positive integer.  

# Solution


### <span id="claim1"></span>Claim 1 ($a = 2$ or $a = 3$)

$$1 < a \leq 3.$$

*Proof.*  
Suppose $a=1$. Then $1 = \left( 1 + \frac{1}{b}\right) \left( 1 + \frac{1}{c}\right) > 1$, a contradiction.  

Expanding $\left( 1 + \frac{1}{a} \right) \left( 1 + \frac{1}{b}\right) \left( 1 + \frac{1}{c}\right)$ 
and applying $a \leq b \leq c$ we have

$$
2 = \left( 1 + \frac{1}{a} \right) \left( 1 + \frac{1}{b}\right) \left( 1 + \frac{1}{c}\right)
= 1+a^{-1}+b^{-1}+c^{-1}+a^{-1}b^{-1}+b^{-1}c^{-1}+a^{-1}c^{-1}+a^{-1}b^{-1}c^{-1} \leq 1 + 3 a^{-1} + 3 a^{-2} + a^{-3},
$$

or $3 a^{-1} + 3 a^{-2} + a^{-3} \geq 1.$

Since $3 a^{-1} + 3 a^{-2} + a^{-3} < 1$ when $a \geq 4$, we get $a \leq 3$.

$\square$






# What I Learned


