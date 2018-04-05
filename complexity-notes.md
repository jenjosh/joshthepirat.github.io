# Algorithms and Complexity

[TOC]

## Introduction

To take algorithms seriously. We start with a problem to solve and ask the following questions:

- How do we design an algorithm to solve it?
- How long will the algorithm take to run?
- How much memory will it use?
- Can we do better?





### Example: Fibonacci series

In a simple example, computing the Fibonacci numbers $F(n)$ is defined by:
$$
F(n)=F(n-1)+F(n-2)
$$
What is the most efficient way to compute this?



#### Recursion

Recursion calls the same function repeatedly.

```python
def F(n):
    if n<=2:
        return 1
    else:
        return F(n-1)+F(n-2)
```

This is very simple and matches the mathematical definition, but very inefficient.

The reason is that you end up repeatedly computing the same thing over and over again. When computing  $F(n)$ you recursively call $F(n-1)$, $F(n-2)$, all the way to $F(1)$.  This problem gets exponentially worse as you continue. In general it will take around $1.6^n$ steps to calculate $F(n)$.



#### Pen and paper algorithm

A better way is store values in a table so you don’t recompute things you’ve already calculated.

```python
def F(n):
    f = [1]*(n-1)	#lis of n+1 zeros
    f[1] = f[2] = 1
    for i in range(3, n+1):
        f[i] = f[i-1]+f[i-2]
    return f[n]
```

This algorithm takes around $n$ steps to compute $F(n)$ but uses a lot of RAM.



#### Iterative algorithm

In the last example we were storing all previously computed values in a table, but we only need the
most recent two values.

```python
def F(n):
	a = b = 1
	for i in range(3, n+1):
		a, b = b, a+b
	return b	
```

This now uses a fixed amount of RAM for any value of $n$.



#### Analytic solution

We can solve the difference equation for $F(n)$ to find that:
$$
F(n)=\frac{\phi^n - (1-\phi)^n}{\sqrt{5}}
$$
Where:
$$
\phi = \frac{1+\sqrt{5}}{2}
$$
Whilst this looks like it will take only a fixed amount of time to find the solution for any $n$, it won't because we need to use more precision for$\phi$ as we increase n, meaning that in the end this takes much longer. 

Double precision only works up to about $n = 70$.



#### Matrix method

The best answer turns out to be a bit obscure, and uses matrices. We let the matrix:
$$
M = \begin{pmatrix}
1 & 1 \\
1 & 0 \\
\end{pmatrix}
$$
And prove by induction:
$$
M^n=\begin{pmatrix} 1 & 1 \\ 1 & 0 \\ \end{pmatrix}^n=\begin{pmatrix} F(n+1) & F(n) \\ F(n) & F(n-1) \\ \end{pmatrix}
$$
We can now calculate $F(n)$ = $(M^n)_{12}$. This takes less than $n$ steps to compute at only $\log_2 n$ steps.

You can use the binary expansion of $n$ to compute $M^n$ for any $n$. For example, if $n = 5 = 0b101$ we calculate $M$, then $M^2$, then $M^4$ and keep a copy of them. Now, we multiply $M$ and $M^4$ to get $M^5$. Since there at most  $\log_2 n$ non-zero bits in the binary representation of n, this algorithm can take at most $ \log_2( n)$ steps.



#####  Theory versus practice

In theory then, the matrix method is the best. Be careful though, because in practice to compute $F(50) $takes about 10 times longer with the matrix method. For large enough n the matrix method will do better, but that value might be very large!



#### Arbitrary sized integers

The iterative algorithm doesn't actually take $n$ steps or use a fixed amount of RAM.

For large $n$, we cannot use fixed size integers, we have to use arbitrary size integers. To store an integer of size $n$ we need to use $\log_2( n)$ bits, and arithmetic operations on them take $O(\log_2( n))$ steps. $F(n) \approx 1.6^n$ so computing $F(n)$ will take an amount of RAM proportional to $n$.

Each arithmetic operation also takes around n steps so the total time is proportional to $n^2$. Similarly, the matrix method will take around $n \log (n)$ steps not $\log( n)$.

In practice, we usually ignore this unless we’re planning to use the algorithm for very large integers
(e.g. when doing cryptography).



#### Context

If we’re only calculating $F(n)$ and we don’t care about the values $F(1), F(2)$, etc. then the matrix method is the theoretically best method. If the task is not to calculate just $F(n)$ but all of $F(1), F(2), . . . , F(n) $ then, the  methods take:

- **Pen and paper** $n^2$ steps.
- **Iterative method** $n^3$ steps.
- **Matrix method** $n^2 \log (n)$ steps.

So now, the best method is the pen and paper method.





## Complexity notation

### Theta Notation

$$
f(n) \text{ is } \Theta(g(n))
$$

####Intuitive Definition

A function $f(n)$ is $\Theta(g(n))$ if $f(n)$ is approximately proportional to $g(n)$. 

This means that:

- **Constant factors can be ignored.** 
  -  So $3n^2$ is $\Theta(n^2)$ because the constant factor can be ignored.
- **Only asymptotic behavior is cared about.**
  - So, for example, $100n + 0.1n^2$ is $\Theta(n^2)$ because eventually, for large enough $n$, the size of $100n + 0.1n^2$ is dominated by the $0.1n^2$ term and the $100n$ term is tiny by comparison. The $\Theta$ notation being asymptotic means that we only care about what happens when $n$ is large.
- **Only the worst case is thought about.**
  - If $f(n) = n$ when $n$ is odd and $f(n) = n^2$ when $n$ is even, then we cannot say that $f(n)$ is $\Theta(n)$ or $\Theta(n^2)$ because it depends whether $n$ is odd or even.



#### Formal Definition

A function $f(n)$ is $\Theta(g(n))$ if there are constants $c_1 > 0$, $c2 > 0$ and $n_0$ such that for all $n \ge n_0$:
$$
0 \le c_1 g(n) \le f(n) \le c_2 g(n)
$$
$$
c_1 > 0 \qquad c_2 > 0
$$

This means that, $f(n)$ has to be sandwiched between two multiples of $g(n)$, but you can ignore a finite
number of initial cases because it only has to be true for all large $n$.



#### Example: $f(n)=n$#

Clearly $f(n) = n$ is sandwiched between $n$ and $n$, so we take $g(n) = f(n) = n$, $c_1 = c_2 = 1$, and this is true for all $n$ so we can take $n_0 = 1$.

We need to check that whenever $n \ge n_0$ something holds, in other words, whenever $n \ge 1$. We need to check that the condition $0 \le c_1g(n) \le f(n) \le c_2g(n)$, which is just $0 \le n \le n \le n$, which is true.

Therefore we have shown that $f(n) = n$ is $\Theta(n)$.



#### Example: $f(n) = n^2 + 10 n \sin{\left(\frac{n}{2}\right)}$

If $n_0 = 50$, $c_1 = 0.8$ and $c_2 = 1.2$ then whenever $n \ge 50$, $f(n)$ is sandwiched between $0.8n^2$ and $1.2n^2$. 

To prove it we use $n_0 = 50$, $c_1 = 0.8$ and $c_2 = 1.2$:

How small can $f(n)$ be:

- The smallest it gets is if $\sin\left(\frac{n}{2}\right) = −1$, in which case $f(n) = n^2 − 10n$. The largest it can get is $\sin\left(\frac{n}{2}\right) = 1$, in which case $f(n) = n^2 + 10n$.

How big can $10n$ be compared to $n^2$:

- Well, $\frac{10n}{n^2} = \frac{10}{n}$. If $n \ge 50$ then this is smaller than $\frac{10}{50} = 0.2$. So $10n \le 0.2n^2$, and therefore $n^2 + 10n$ must be between $0.8n^2$ and $1.2n^2$.




####Example: $f(n)=n \sin^2\left(\frac{n\pi}{2}\right)$ 

If n is odd then $f(n) = n$, however if $n$ is even then $f(n) = 0$. So, if we had a constant $c_1$ with $0 \le c_1n \le f(n)$ then, when $n$ was even, we would have to have that $c_1 = 0$. 

However, part of the definition is that $c_1 > 0$. So we cannot say that $f(n) = \Theta(n)$ in this case.



### Big O notation

In terms of a program, you can think of this as saying that it **takes at most $g(n)$ steps to run**.

A function $f(n)$ is $O(g(n))$ if there are constants $c > 0$ and $n_0$ such that when $n \ge n_0$:
$$
0 \le f(n) \le c g(n)
$$


### $\Omega$ notation

$f(n)$ is $\Theta(g(n))$ if $f(n)$ is greater than $\Theta(g(n))$. For a program, it **takes at least this long to run**.

A function $f(n)$ is $\Omega(g(n))$ if there are constants $c > 0$ and $n_0$ such that when $n \ge n_0$:
$$
0 \le c g(n) \le f(n)
$$


### Notes

- $f(n)$ is $\Theta(g(n))$ if and only if $f(n)$ is $O(g(n))$ and $\Omega(g(n))$.
- To say $f(n)$ is $O(g(n))$ all we have to do is sandwich $f(n)$ between $0$ and a multiple of $g(n)$. In other words, $f(n)$ has to be less than some constant multiplied by $g(n)$. 
- Similarly, $f(n)$ is $\Omega(g(n))$ if $f(n)$ is larger than some constant multiplied $g(n)$.



### Big O and $\Omega$ notation examples

#### Example: $f(n)=n \sin^2\left(\frac{n\pi}{2}\right)$

We saw before that we couldn’t say $f(n)$ is $\Theta(n)$. However, we can say that $f(n)$ is $O(n)$ because taking $c = 1$ and $n_0 = 1$ we always have that $\sin^2\left(\frac{n\pi}{2}\right) \le 1$ and therefore $n \sin^2\left(\frac{n\pi}{2}\right) \le n$.



#### Compound example, $f(n) = n + n^2 \sin^2\left(\frac{n\pi}{2}\right)$

We have for n even that $f(n) = n$ and for $n$ odd that $f(n) = n + n^2$. So, we can always find a constant $c$ so that $f(n) \le cn^2$ and therefore $f(n) = O(n^2)$.

We can also see that it’s always true that $f(n) \ge n$, and so $f(n) = \Omega(n)$. We can’t say that $f(n) = Θ(n)$ or $Θ(n^2)$ though.

Is there a function $g(n)$ so that $f(n) = Θ(g(n))$?

Actually yes, but it’s a bit pointless. For any function $f(n)$ it’s always true that $1 ·f(n) ≤ f(n) ≤ 1·f(n)$, so let $g(n) = f(n)$ and $c_1 = c_2 = 1$ and it’s always true that $c_1g(n) ≤ f(n) ≤ c_2g(n)$. In other words, it’s always true that $f(n) = Θ(f(n))$.



### Little $o$  and little $\omega$ notations

A function $f(n)$ is $o(g(n))$ if **for any** constant $c > 0$ there is an $n_0$ so that for $n > n_0$:
$$
0 ≤ f(n) < cg(n)
$$
A function $f(n)$ is $ω(g(n))$ if **for any** constant $c > 0$ there is an $n_0$ so that for $n > n_0$:
$$
0 ≤ cg(n) < f(n)
$$


### $\mathbf{O(1)}$ Algorithms

An algorithm that is $O(1)$ takes a fixed amount of time, regardless of the value of $n$. These are kind of rare. Examples are things like computing whether or not $n$ is odd or even (just look at the last bit). 

In practice we usually assume that arithmetic operations are $O(1)$. In reality, even calculating $n+1$ is actually $O(\log (n))$.



### $\mathbf{O(\log n)}$ Algorithms

$\log n$ grows very slowly. For example:
$$
\log_2(2n) =\log_2( 2) +\log_2( n) = 1 + \log_2( n)
$$

Note that whenever we’re talking algorithmic complexity, we don’t need to specify the base of the logarithm because different bases are just multiplication by a constant $\log_b( x) =\frac{ \log x}{ \log b}​$, and with complexity notation we can ignore all constant factors.

A good example of an algorithm that is $O(\log (n))$ is binary search in a sorted array.

In practice, factors of \log n are usually so small compared to everything else that we often ignore them. There is even a notation for this. We say that $f(n) =\tilde{ O}(g(n))$ if $f(n) = O(g(n) \log (n))$ or $f(n) = O(g(n)(\log (n))^2)$, etc. This is pronounced soft-O. 

Note though that in this course, you may not use soft-O notation or ignore factors of $\log n$!



### $\mathbf{O(n)}$ and $\mathbf{O(n\log n)}$ Algorithms

These are very common and desirable algorithms because they scale with the size of the data (or almost with the size of the data), and this is usually the best we can hope for. 

Examples include finding the maximum value of an unsorted array ($O(n)$) or sorting an array (merge sort is $O(n \log (n))$).



### Examples of higher order polynomial algorithms

These are algorithms that are $O(n^2)$,  $O(n^3)$, etc. 

Examples include matrix multiplication, which is $O(n^3)$ but with a clever trick can be reduced to $O(n^{2.4})$.



### Examples of exponential or worse algorithms

These are algorithms that are $O(2n)$, $O(n!)$, $O(n^n)$, etc.

Examples probably include the travelling salesman problem, although that’s not been proven.



### Comparing logarithms, polynomials and exponentials

Broadly speaking, constants are always smaller (in terms of complexity) than logarithms, which are always smaller than polynomials, which are always smaller than exponentials. Here’s how we can prove that.

We start by proving that for any $a > 1$ and $b > 0$, $n^b = o(a^n)$ (note the little-o notation).

To prove this, we expand:

$$
a^n = e^{n \log a} = 1 + n \log a + \frac{(n \log a)^2}{2!} + \frac{(n \log a)^3}{3!} + ...
$$

Eventually, on the right hand side there will be a term $\frac{(n \log a) k}{k!}$ for some $k > b$. So we know that $a^n > $some constant $n^k$ where $k > b$. So we know that (ignoring constants), $n^k$ is smaller than $a^n$. And since $k > b$, $n^b$ = $o(n^k )$ so $n^b = o(a^n)$. 

This shows that any polynomial is smaller than any exponential.

If we replace $n$ by $\log n$ in these equations we get that, for any $b > 0$ and $\epsilon > 0$ (set $a = e^{\epsilon}$ ): 
$$
(\log n)^b = o(n^{\epsilon} )
$$

Therefore, any power of any logarithm is smaller than any polynomial.





## Divide and Conquer

Divide and conquer is a general strategy for designing algorithms. The basic idea is to:

- **Divide** problem into two pieces.
- **Conquer** (solve) those pieces independently.
- **Combine** the solutions.



For this to work it must be possible to:

- Divide into independent subproblems.
- Conquer subproblems more easily than original problem.
- Combine solutions without doing too much work.




###Numerical Example

Let’s look at a numerical example to demonstrate how dividing and conquering can help. Suppose we have an algorithm that takes $n^2$ steps to run on n data, but where if we have already run the algorithm on the first half and the second half of the data, we can combine them in only n steps to get the result on the whole data set.

Take $n = 128$. Running the algorithm on the whole data set will take $128^2 = 16, 384$ steps. How about if we divide into two pieces, run the algorithm on those halves, and combine? Well, the two pieces will have $n = 64$ so running the algorithm on these will take $64^2 = 4, 096$ steps each, or $8, 192$ steps total. Combining those will take $n = 128$ steps. So the total time will be $8, 320$ steps. So dividing, conquering and combining has almost halved the number of steps required.

If we divide $k$ times, we have $2^k$ subproblems which cost $\left(\frac{n}{2^k }\right)^2 $ each, and we have to do $nk$ steps of combining. So the total cost is $2^k \left(\frac{n}{2^k} \right)^2 + nk = \frac{n^2}{2^k} + nk$. 

We can only keep subdividing until the size of the subproblems is $1$, i.e. $\frac{n}{2^k} = 1$. This gives $k = \log_2 n$. 

Substituting into the formula above, the total cost will be $n + n \log_2 n = O(n \log n)$. In other words, we’ve reduced from $O(n^2 )$ to $O(n \log n)$.



### Worked Example: maximum subarray problem

Let’s now turn to a worked example of a divide and conquer algorithm. 

A generous but didactic genie tells you what the share price for a particular stock will be over the next week, on condition that you are only allowed to buy and sell once during that period. What is your best strategy to maximise your profit?



#### Naïve maximum strategy

We slightly change this problem to be about maximising the sum of a contiguous subarray of a
given array X. Here X will be the difference in stock prices between one time and the next. A
naive way of solving this problem is to loop over every possible start and end time, compute the
sum, and find the maximum:

```python
def brute_force_max_subarray(X):
	n = len(X)
	best_sum = 0
	best_i = 0
	best_j = 0
	for i in range(n): 				# n times
		for j in range(i+1, n):		# n-i times
			cur_sum = sum(X[i:j]) 	# O(n)
			if cur_sum>best_sum:
				best_sum = cur_sum
				best_i = i
				best_j = j
	return best_sum, best_i, best_j	
```

This works, but is $O(n^3 )$. The outer loop is repeated n times. The inner loop is repeated $(n−i) $ times, which is less than $n$. The sum is at most $n$ items, so is $O(n)$. So the total is $O(n × n × n) = O(n^3 )$.

You might wonder if it should be smaller than this, because the inner loop is only repeated $(n−i)$ times not $n$ times, and $( n − i)$ will sometimes be as small as $1$. Actually, it doesn’t change the complexity. You can see this because the total number of loops will be $ n + (n − 1) + (n − 2) + · · · + 3 + 2 + 1$ and it’s a standard formula that the sum of the first $n$ integers is $\frac{n(n + 1)}{2}$ which is $O(n^2 )$.

We can make this algorithm more efficient by removing the sum calculation, and computing the
sum cumulatively as we go:

```python
def better_brute_force_max_subarray(X):
	n = len(X)
	best_sum = 0
	best_i = 0
	best_j = 0
	for i in range(n): # n times
		cur_sum = 0
		for j in range(i, n+1): # n-i times
			if cur_sum>best_sum:
				best_sum = cur_sum
				best_i = i
				best_j = j
			if j<n:
				cur_sum += X[j]
	return best_sum, best_i, best_j
```

Now the inner loop code is only $O(1)$ instead of $O(n)$ and so the total is just $O(n^2)$.



#### Divide and conquer algorithm for maximum subarray

We divide the array into two halves at the midpoint. The maximum subarray of the whole array
must be ONE of the following:

- Entirely contained within the first half.
- Entirely contained within the second half.
- Must pass through the mid point.

The first two cases will be found by the divide part of the algorithm. We also have to make sure that we cover the third case, where the best subarray is partly in the first and partly in the second halves. This looks like it’ll be just as hard as the main problem and therefore be $O(n^2 )$, but there’s a clever trick. Since we know it must pass through the mid point, we can start with our best subarray starting and ending at that midpoint, enlarge it as much as possible to the left and then to the right. In other words, first we iterate through the first $ \frac{n}{2}$ start points, and maximise the sum up to the midpoint. Then, we iterate through the second $\frac{n}{2}$ start points and maximise the sum from the start point to this end point. We can only do this because we know that in this case, we must go through the midpoint.

So now, if we combine these three operations, we divide into two equally sized subarrays, find the maximum subarrays for these two, and then find the maximum subarray that passes through themidpoint. Finally, we return the best of these three options. The “combine” step is taking $O(n)$ steps. 

```python
def dac_maxsubarray(X):
	if len(X)<=1: 											# BASE CASE
		return sum(X), 0, len(X)
	mid = len(X)/2 											# DIVIDE
	left_sum, left_i, left_j = dac_maxsubarray(X[:mid]) 	# CONQUER LEFT
	right_sum, right_i, right_j = dac_maxsubarray(X[mid:]) 	# CONQUER RIGHT
	# Correct for relative indices
	right_i += mid
	right_j += mid
	cursum = mid_sum = 0 									# CONQUER MIDDLE
	mid_i = mid_j = mid
	for i in range(mid-1, -1, -1): 		# i from mid-1 to 0 # Start from mid
		cursum += X[i] 										# and move left
		if cursum>mid_sum:
			mid_sum, mid_i = cursum, i
	cursum = mid_sum
	for j in range(mid+1, len(X)+1): 	# j from mid+1 to n # Start from mid
		cursum += X[j-1] 									# and move right
		if cursum>mid_sum:
			mid_sum, mid_j = cursum, j
	if left_sum>=right_sum and left_sum>=mid_sum: 			# COMBINE
		return left_sum, left_i, left_j
	elif right_sum>=mid_sum:
		return right_sum, right_i, right_j
	else:
		return mid_sum, mid_i, mid_j
```

How many steps does this take? Well, the naive algorithm is $O(n^2 )$, we divide always into two equal halves, and the combining step is $O(n)$, so it’s exactly the same as the hypothetical case we considered above. So this algorithm will take $O(n \log n)$ steps to run.



#### Proving it with induction

How could we prove that this is $O(n \log n)$? In our calculation earlier, we assumed the number of steps was exactly n 2 and n for combining. Now we’re only assuming it’s $O(n^2 ) $ and $ O(n)$. We will see a better method later, but we can start by just guessing that since the constants probably don’t matter, it’ll probably be the same answer $O(n \log n)$.

Let’s write $T(n)$ for the number of steps this divide and conquer algorithm takes. We know that it proceeds by dividing into two equal halves, and solving them first, and then combining over $O(n)$ steps. So we can write that:
$$
T(n) = 2T\left(\frac{n}{2}\right) + O(n)
$$

This sort of formula will become important later. What does it mean when we write that out with explicit constants? It means that for some large enough $n_0$ and some constant $c$, whenever$ n ≥ n_0$ we have:
$$
T(n) ≤ 2T\left(\frac{n}{2}\right) + cn
$$

We want to prove that $T(n) = O(n \log n)$, which would mean that there’s some constants $n_0$ and d so that whenever $n ≥ n_0$ we have:
$$
T(n) ≤ dn \log_2 n
$$

Note here that we know that first two equations are true, and we want to prove that the third equation is true. We will use proof by induction, or rather a slight variant of this called proof by strong induction.

In this case, to prove statement $P(n)$ we need to prove:

- $ P(1)$ and that if $P(m)$ is true for all $m < n$ 
- $P(n)$ is true. 

If we can prove these two statements (called the base case and induction step) we have proved $P(n)$ for all $n$.

In our case, we’ll start with $n = 2$ rather than $n = 1$ because when $n = 1$ the third equation would say $T(n) ≤ 0$ which can’t be true. Also note that we’re going to assume $n_0 = 2$. This is partly to simplify the proof, but it doesn’t change anything. If the second equation is true for some $n_0$, by increasing the size of the constant $c$ we can make it true for $n_0 = 2$ (because $n \log n$ is a monotonically increasing function: we can’t always do this).

So when $n = 2$, the third equation states that $T(2) ≤ 2d \log_2 2 = 2d$. Note that we haven’t yet said what $d$ is. We only need to find some constant d that makes the third equation true, so let’s just note that whatever value of $d$ we want, it should be at least as big as $\frac{T(2)}{2}$.

Now assume the third equation is true for all $m < n$, in particular it is true for $m = \frac{n}{2}$ (this will be our induction assumption). In other words, $T(\frac{n}{2}) ≤ \frac{dn}{2} · \log_2 \left(\frac{n}{2}\right)$. We now start with the second equation and use this induction assumption to simplify it:
$$
T(n) ≤ 2T\left(\frac{n}{2}\right) + cn	 \qquad	 \qquad	\text{Definition of }T(n)
$$

$$
≤ 2d\left(\frac{n}{2}\right) \log_2 \frac{n}{2} + cn 	 \qquad	\text{Induction assumption}
$$

$$
= dn(\log n − \log_2 2) + cn \qquad \qquad  \qquad\qquad \qquad \;
$$

$$
= dn \log n + (c − d)n  \qquad \qquad \qquad \qquad \qquad \quad \; \; \; \;
$$

$$
≤ dn \log n  \qquad \qquad \qquad  \qquad\qquad \qquad \quad \; \;\text{if }d > c
$$

Note that last line (which is what we want to prove) is only true if $d > c$, so again we note that whichever $d$ we choose it should be at least as large as $c$. Now however, we can see that the whole argument works as long as:

- $d > \frac{T(2)}{2}$.
- $d > c$. 

So let’s just choose $d = 2 max\left\lbrace \frac{T(2)}{2}, c\right\rbrace$. With this choice of $d$, all the arguments above hold and the proof is complete. 

This method works well if you can guess the answer, but that’s not always obvious. Next, we’ll turn to a more general method for analysing divide and conquer type algorithms.



### The Master Method

The Master Method gives a formula for the running time of a divide and conquer algorithm based on the size and number of subcases, and how much work it takes to combine them. If:
$$
T(n) = a T\left( \frac{n}{b} \right) + O(n^d)= \left\lbrace \begin{matrix} a & \text{Number of subcases} \\ \frac{n}{b} & \text{Size of each subcase} \\ O(n^d) & \text{How long it takes to combine} \end{matrix} \right.
$$
For some $a > 0$, $b > 0$ and $d ≥ 0$, then:
$$
T(n) = \left\lbrace \begin{matrix} O(n^d) & \text{if }d>\log_b a \\ O(n^d \log n) & \text{if }d=\log_b a \\ O(n^{\log_b a}) & \text{if }d<\log_b a\end{matrix} \right.=\overline{O} \left(n^{max(d,\log_b a)}\right)
$$
We can now see the example we looked at in the previous section, including the maximum subarray problem, satisfies the equation $T(n) = 2T\left(\frac{n}{2}\right) + O(n)$. This is the general equation above with $a = b = 2 $ and $d = 1$. So, to compute the solution we need to check the value of $\log_b a =\log_2 2 = 1$. This is equal to $d$, and therefore we’re in the middle case, so $T(n) = O(n^d \log n) = O(n \log n)$, as we already proved.

Another example comes from Strassen’s matrix multiplication algorithm. Normally, multiplying two $n × n$ matrices takes $O(n^3 )$ steps. However, Strassen’s algorithm uses a divide and conquer approach to reduce this. We won’t cover it here, but just note that with this algorithm it’s easy to show that $T(n) = 7T\left(\frac{n}{2}\right) +O(n^2 )$. In other words, we now divide into seven subcases, each of size $\frac{n}{2}$, and combining is harder ($O(n^2 )$ instead of $O(n)$). We can use the Master Method to compute the running time. First we note that $a = 7$, $b = 2$, $d = 2$. We compute $\log_b a = \log_2 7 ≈ 2.8 > d = 2$. So we’re in the third case, and $T(n) = O(n \log_b a ) = O(n^{2.8} )$. So this algorithm reduces the running time from $O(n^3 )$ to $O(n^{2.8} )$.



#### Merge sort

The well known merge sort algorithm is actually an example of a divide and conquer algorithm, and we’ll go through this to illustrate divide and conquer again. We want to take an array $X$ and return a sorted version of it. We first divide it into two equal halves, and sort those. Now, given two sorted arrays, how can we combine those into a single sorted array in as few operations as possible? Well, the first step is to check the first item of both sorted arrays, and take the smaller of the two and make that the first item of the whole sorted array. This must be correct, because the first item of the two smaller sorted arrays are the smallest values of each of them, so the smaller of them both must be the first item of the whole sorted array. Now, we delete the item that we added to the whole sorted array from whichever of the two smaller sorted arrays it came from. And now we just repeat this process until there are no items left. This will take at most $n$ steps. So with this algorithm, we will again have that the running time $T(n) = 2T\left(\frac{n}{2}\right) + O(n)$ and therefore $T(n) = O(n \log n)$. 

```python
def dac_mergesort(X):
	if len(X)<=1: # BASE CASE
		return X
	mid = len(X)/2 # DIVIDE
	sorted_left = dac_mergesort(X[:mid]) # CONQUER
	sorted_right = dac_mergesort(X[mid:])
	out = empty_like(X) # Allocate an array of same size/type as X
	i = j = k = 0 # COMBINE
	while i<len(sorted_left) or j<len(sorted_right):
		if i==len(sorted_left): # All left entries added to out
			out[k] = sorted_right[j]
			j += 1
		elif j==len(sorted_right): # All right entries added to out
			out[k] = sorted_left[i]
			i += 1
		else: # Add the smaller of left/right to out
			left = sorted_left[i]
			right = sorted_right[j]
			if left<=right:
				out[k] = left
				i += 1
			else:
				out[k] = right
				j += 1
		k += 1
	return out
```



#### Merge sort is optimal

Amazingly, it turns out that this is the best we can do for a general sorting algorithm where the only operation we can carry out on the items we want to sort is to check, for a given pair $a$ and $b$, if $a < b$. 

Sometimes, we can do better than this (for example, in arrays of integers), and then there are better sorting algorithms. We’ll show here though that for a general sorting algorithm that only has access to comparisons, this is the best you can do. If we want to sort an array of $n$ elements, there are $n!$ possible ways to order those $n$ elements. To sort it, we need to work out which of these n! possible orderings is the correct one. Each time we perform a comparison $a < b$ on two items $a$ and $b$ from the array, at best we reduce the number of possible orderings by half. So this means that in the worst case, we’ll need $\log_2 n!$ comparisons. We can show that $\log_2 n! = Θ(n \log n)$, and therefore sorting with comparisons is worst case $Ω(n \log n)$. So, since merge sort is $O(n \log n)$, it is therefore the best we can do.



##### Proof that $\log_2 n! = Θ(n \log n)$

$$
n! = n · (n − 1) · (n − 2)· ... · 3 · 2 · 1
$$

Using $\log xy = \log x + \log y$ we can expand this as:
$$
\log n! = \log n + \log(n − 1) + \log(n − 2) +... + \log(3) + \log(2) + \log(1).
$$

Each term in this sum is $≤ \log n$ and there are $n$ terms, and and therefore $\log n! ≤ n\log n$. This means that $\log n! = O(n \log n)$. We also need to prove that $ \log n! = Ω(n \log n)$. To do this, note that:
$$
\log n! = \log n + \log(n − 1) + \log(n − 2) + ... + \log(3) + \log(2) + \log(1)
$$

$$
≥ \log n + \log(n − 1) + \log(n − 2) + ... + \log\left(\frac{n}{2}\right)
$$

In other words, if we throw away the last half of the terms in the sum, the whole sum will be larger than this. Now each term in this half-sum is $≥ \log\left(\frac{n}{2}\right)$ and there are $\frac{n}{2}$ terms, so $\log n! ≥ \left(\frac{n}{2}\right) \log\left(\frac{n}{2}\right) = \left(\frac{n}{2}\right)(\log n − \log 2)$ and therefore (since we can throw away constants) $\log n! = Ω(n \log n)$. Finally, since it is both $O$ and $ Ω$ it must be $Θ$.

Note that the same trick can be used to show that $Θ(1) + Θ(2) + ... + Θ(n − 1) + Θ(n) = Θ(n^2)$.



#### Karatsuba's algorithm

Suppose we want to write efficient code to multiply two n-bit integers (where $n$ can be larger than the size of a hardware integer). The naive algorithm would be to do long multiplication in binary, similar to what is done when you learn that at school. 
However, this algorithm is $O(n^2 )$: each row in the calculation is $O(n)$ and there are $n$ rows. Can we do better? We can use divide and conquer. Divide the $n$-bit integer $X$ into the lower and upper halves of the binary representation. Call these $x_0$ for the lower half, and $x_1$ for the upper half. So, $x_0$ and $x_1$ are both $\frac{n}{2}$-bit integers, and $X = x_1 2^{\frac{n}{2}} + x_0$. Now write another integer $Y = y_1 2^{\frac{n}{2}} + y_0$ and multiply these to get:
$$
XY = (x_1 2^{\frac{n}{2}}  + x_0)(y_1 2^{\frac{n}{2}}  + y_0) = x_1 y_1 2^n + (x_1 y_0 + x_0 y_1)2^{\frac{n}{2}}  + x_0 y_0
$$

Each of the multiplications $x_1y_1$, $x_1y_0$, $x_0y_1$ and $x_0y_0$ is an $\frac{n}{2}$-bit multiply, and the remaining operations are shifts and adds which can each be done in $O(n)$ steps. Therefore, we can see that the running time for this algorithm is:
$$
T(n) = 4T\left(\frac{n}{2}\right) + O(n).
$$

Applying the Master Method, we have $a = 4$, $b = 2$, $d = 1$. We calculate $\log_b a = \log_2 4 = 2 > d = 1$. Therefore, $T(n) = O(n \log_b a ) = O(n^2 )$. Unfortunately, divide and conquer has gained us nothing here!

But there’s a trick we can use. We note that:
$$
x_1y_0 + x_0y_1 = (x_1 + x_0)(y_1 + y_0) − x_1y_1 − x_0y_0.
$$

At first, this looks like we’ve made more work for ourselves, instead of two $\frac{n}{2}$-bit multiplies, we now have to do $(x_1 + x_0)(y_1 + y_0)$, $x_1y_1$ and $x_0y_0$, or three multiplies. However, if we look at the whole picture, we can re-use $x_1y_1$ and $x_0y_0$, and these three multiplies are all we need for the whole formula. In other words we compute:
$$
a = x_0y_0
$$

$$
b = x_1y_1
$$

$$
c = (x_1 + x_0)(y_1 + y_0)
$$

$$
XY = b 2^n + (c − a − b)2^{\frac{n}{2}} + a
$$

Computing each of $a$, $b$ and $c$ is an $\frac{n}{2}$-bit multiply, but then computing $XY$ is just shifts and adds. So now $T(n) = 3T\left(\frac{n}{2}\right) + O(n)$ and this gives $\log_b a = log_2 3 ≈ 1.58 > 1 = d$ and so $T(n) = O(n^{1.58})$ which is better than the naive $O(n^2 )$.



#### When not to use the Master Method

If you have the equation $T(n) = T(n − 1) + O(1)$, it looks like you might be able to apply the Master Method. You can set $a = 1$ and $d = 0$, but what about $b$? There is no value of $b$ such that $\frac{n}{b} = n − 1$, so the Master Method doesn’t apply.

What do you do in this case? Simply compute it by hand.

$T(n) = T(n − 1) + O(1)$ means there is a constant $c$ such that $T(n) ≤ T(n − 1) + c$. However, it also means $T(n − 1) ≤ T(n − 2) + c$ and so on. Subsituting this into the previous equation we get $T(n) ≤ T(n − 1) + c ≤ T(n − 2) + c + c = T(n − 2) + 2c$. Continuing in this way we get $T(n) ≤ T(0) + nc$, and since $T(0)$ is a constant, $T(n) = O(n)$.



#### Where does the Master Method come from?

Divide and conquer has two types of work. It has:

- The work done in combining subcases. 
- The work done in the last step when the cases have size 1. 

If we add these together, we get the total work done.

First, consider the work done in the last step. At step $k$, there are a $k$ cases, each has size $\frac{n}{b^k}$. At the final step, $\frac{n}{b^k} = 1$ so $k = \log_b n = \frac{\log n}{\log b}$. So the total work done is:
$$
a^k = e^{k \log a} = e^{\log n \frac{\log a}{\log b}} = e^{\log n \log_b a} = n^{\log_b a}
$$

In other words, the total work done is $n^{\log_b a}$.

How about the work done in combining? The last bit of combining we will do is one time $O(n^d )$. The second-last bit of combining will be a times $\left(\frac{n}{b}\right) d$ , and so on. The total work (dropping the $O$ notation) will be:
$$
n^d + a\left(\frac{n}{b}\right)^d + a^2 \left(\frac{n}{b^2} \right)^d +...+ a^{k−1} \left(\frac{n}{b^{k−1}} \right)^d 
$$

Writing $α = \frac{a}{b^d}$ we can simplify this to:
$$
n^d (1 + α + α^2 + ... + α^{k−1} )
$$

This is just a geometric series, and so the solution is:
$$
n^d\frac{\alpha^k - 1}{\alpha - 1}
$$

If $d > \log_b a$ then take $b$ to the power of both sides to get that $b^d > a$ and therefore $α < 1$. In this case, when $k$ is large (which will happen when $n$ is large), $α^k → 0$ and therefore the work done in combining will be $\frac{n^d}{(1 − α)} = O(n^d )$.

If $d < \log_b a$ then $α > 1$ and we can ignore the $−\frac{1}{(α − 1)}$ term to get the total work done in combining being:
$$
O(n^dα^{k−1} ) = O(n^dα^k ) = O(e^{d \log n+k \log α} ) 
$$

$$
= O(e^{\frac{d \log n+\log n}{\log b(\log a−d \log b)}} ) 
$$

$$
= O(e^{\frac{\log n \log a}{ \log b}} ) 
$$

$$
= O(n^{\log_b a} ).
$$

This shows what happens when $d \ne \log_b a$: handling the case $d = \log_b a$ is a little bit more complicated. However, this should give some idea as to why the slightly bizarre quantity $log_b a$ crops up in the Master Method.





## Dynamic programming

Dynamic programming is another recipe - like divide and conquer - for creating efficient algorithms.
We saw that for divide and conquer we wanted to break a large problem into independent subproblems
so we could solve those and combine their solutions. We do something similar with dynamic
programming, but in this case we divide into non-independent, overlapping subproblems.

Specifically, we use dynamic programming for optimisation problems with optimal substructure. By
optimisation problems, we mean problems where we want to make a set of choices to maximise
some sort of value. Those choices could be about what products we choose to make in a business,
or what prices we want to sell them at, for example.

Optimal substructure means that if we know the optimal solution to the whole problem, we should
be able to use this to find the optimal solution to a subproblem. This seems counterintuitive because
we want to go from knowing solutions to smaller problems to finding solutions to larger problems,
but actually this optimal substructure property lets us do that.

The way dynamic programming algorithms work then is to iterate through all the different ways of
breaking a large problem into smaller subproblems. We recursively find the optimal solutions for
these, and efficiently store the results (more on this later). Once we know the optimal solutions for
all the possible subproblems, we can choose the optimal way of combining them. Let’s move on to
an example.



### Example: Rod cutting

The exciting premise of this example is that you are the director of a company that manufactures and sells metal rods. Your factory produces rods that are 8m long, and you can sell them for £20 each. One day you notice that other companies are selling 4m long rods for £15 and people are buying them. What do you do?

Obviously, you cut all your rods in half before selling them. Now, instead of getting £20 for each rod produced, you get £30. Profit! Time goes by, and 4m long rods go out of fashion. The price for them now is just £9. Your previous strategy of cutting all your rods in half is now losing you money. You could just go back to selling 8m long rods. Instead, you decide to survey the market and see what prices rods of different lengths are selling for. Here’s what you find. What is your optimal strategy now?

| Length $i$  |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |
| :---------: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| Price $p_i$ |  1   |  5   |  8   |  9   |  10  |  17  |  17  |  20  |

In this case, can just see that cutting them into two rods of length 2m and 6m makes £17+£5=£22 per rod, and this is the best solution. What about the general case (rod of length $n$, price for length $i$ is $p_i$).



#### Brute force solution

The simplest thing to try would be just to look at all possible ways and see which is best. The order of complexity is $Ω(2^n)$ because there $2^{n−1}$ ways of cutting the rod (you can cut at the 1m mark, the 2m mark, the 3m mark, all the way up). This isn’t good, but works for the example above just because n is so small. Here’s some code:

```python
def rod_cut_brute_force(p):
	n = len(p)
	best = None
	bestprice = -inf
	for i in range(2**(n-1)):
		curcut = []
		curlength = 0
		for j in range(n):
			curlength += 1
			if i & 1: # make a cut
				curcut.append(curlength)
				curlength = 0
			i = i >> 1
		curcut.append(curlength)
		curprice = sum(p[k-1] for k in curcut)
		if curprice>bestprice:
			best = curcut
			bestprice = curprice
	return bestprice, best
```



#### Dynamic programming solution

Now we’ll illustrate dynamic programming by applying it to this example. We start by solving a simpler problem: what is the best price $V_n$ we can achieve for a rod of length $n$? That is, we don’t want to know how to achieve the best price, but just what that price should be. We can set this up as a mathematical equation.

We know that we are going to have to start by cutting off some length of the rod and selling that piece. Suppose that the first piece we cut off has length $i$. In that case, the best price we would get is the price from making the cut of length $i +$ the best possible price we could get from a rod of length $ n − i$. The price for the length $i$ piece is $p_i$ and the best we can get from the remaining rod of length $n − i$ is $V_{n−i}$ . In other words, making a cut of length $i$ will give us a total price of $p_i + V_{n−i}$ . So now we consider all the possible first cuts $i$ we could make and choose the best one. This gives us that the best price we can get is:
$$
V_n=max_i (p_i+V_{n-i})
$$

Note that this is precisely what we mean by optimal substructure: the best solution for $n$ is built from the best solutions of subproblems (in this case the rods of length $n − i$).

It’s easy to turn this equation into an algorithm, we just turn the maxi into a loop over $i$, and $V_n$ into a function that we call recursively. Note that we add the extra information that:

- we know that $V_0 = 0$ without having to apply the formula, because a rod of length $0$ has $0$ value.
- we know $V_1 = p_1$ because we can’t cut a rod of length $1$ any smaller. We incorporate this into the code:

```python
def rod_cut(n, p):
	if n==0:
		return 0
	elif n==1:
		return p[0]
	else:
		bestprice = 0
		for i in range(1, n+1):
			curprice = p[i-1]+rod_cut(n-i, p)
			if curprice>bestprice:
				bestprice = curprice
		return bestprice
```

This algorithm works, but it’s inefficient for the same reason that the recursive Fibonacci code is inefficient. It repeatedly computes the same values over and over again. However, we can solve this problem in precisely the same way as we did for the Fibonacci code: by storing the values we’ve already computed. We’ll illustrate this with a more general approach called memoisation.



#### Memoisation

Memoisation just means modifying a function so that it stores the result of a computation so that if the function is called with the same arguments again, it can just retrieve the stored version rather than recalculate it.

A very general way of doing this is using a data structure called a hash table. A hash table is a data structure $T$ that stores mappings from keys `k` to values `T[k]`.Insertion, deletion and lookup are all typical case $O(1)$ (although worst case $O(n)$). Here is an implementation of the Fibonacci series using a hash table rather than an array to store the precomputed values.

```python
def fib(n, memo=None):
	if memo is None:
		memo = {1:1, 2:1}
	if n not in memo:
		memo[n] = fib(n-1, memo)+fib(n-2, memo)
	return memo[n]
```

This approach is a little different to what we did before. Now, when we call `fib(n)`, it first creates a hash table memo and sets `memo[1] = memo[2] = 1` (corresponding to `F(1) = F(2) = 1`). Now, if `n` is not in the table, it computes it recursively and stores it in the table, and then finally returns the value from the table. So if we called `fib(5)` for example, it would first create memo, then ask for `fib(n-1)` (second last line). This is `fib(4)`. `4` is not in memo so it would ask for `fib(3)`. `3` is not in memo so it would ask for `fib(2)`. Finally, `2` is in memo so `fib(2)` would just return the value `1`. Next, the `fib(3)` function call would ask for `fib(n-2)` or `fib(1)`. Again, `1` is in memo so this would immediately return `1`. Now, the `fib(3)` recursive function calls are complete, it would evaluate the expression `fib(n-1)+fib(n-2)` to `2`, store than in `memo[3]` and then return that value. At that point, any future calls to `fib(3)` will immediately return the value `2`. Execution would continue up to the `fib(4)` function call, and so on.

In this example, we started from the top `fib(n)` and recursively found our way to the bottom `fib(1)` and `fib(2)`. In our previous versions, we started from the bottom at `fib(1)` and `fib(2)` and then work up to `fib(n)`. These two approaches are called top-down and bottom-up. In general, bottom-up is more efficient if you know the order of which computation depends on what, and if you know you’ll need to compute all the values to get the last one. If you can’t give the keys a nice simple integer order (for example, you’re writing an algorithm that works on graphs which can’t be easily mapped to integers), or if you don’t know what order and which keys will be used, you have to use the top-down approach. In terms of algorithmic complexity, they’re both equivalent, so it’s only a matter of practical efficiency.



#### Dynamic programming with memoisation

We can now rewrite our dynamic programming solution to the rod cutting problem using memoisation.

```python
def rod_cut(n, p, memo=None):
	if memo is None:
		memo = {0: 0, 1: p[0]}
	if n not in memo:
		bestprice = 0
		for i in range(1, n+1):
			curprice = p[i-1]+rod_cut(n-i, p, memo)
			if curprice>bestprice:
				bestprice = curprice
		memo[n] = bestprice
	return memo[n]
```

What is the complexity of this algorithm? Well, a particular call to `rod_cut(n)` will either take $O(1)$ steps if $n$ is in memo, or $O(n)$ steps if not (because it iterates from $1$ to $n$). Note that this is only taking into account the time spent in each function call, not the time spent in the functions it recursively calls. Next, we can see that we will need to compute `rod_cut(i)` for all $i$ from $1$ to $n$. Each one is $O(n)$ and there are $n$ of them, so the total cost is $O(n^2 )$. This isn’t great because $O(n^2 )$ algorithms are still quite expensive, but it’s a lot better than the $Ω(2^n)$ algorithm we started with!



#### Full solution

What this doesn’t answer is which cuts we should make, only how much we would make if we were to do it optimally. Fortunately, it’s very easy to fix this. We simply memoise the list of cuts along with the price. Here’s some code:

```python
def rod_cut(n, p, memo=None):
	if memo is None:
		# Initialise memo dictionary
		# n value list of cuts
		memo = {0: (0, [] ),
				1: (p[0], [1] )}
	if n not in memo:
		bestprice = 0
		bestcuts = None
		for i in range(1, n+1):
			best_subprice, best_subcuts = rod_cut(n-i, p, memo)
			if p[i-1]+best_subprice>bestprice:
				bestprice = p[i-1]+best_subprice
				bestcuts = [i]+best_subcuts
		memo[n] = (bestprice, bestcuts)
	return memo[n]
```

The complexity of this algorithm is the same, but it uses a lot of memory to store all the solutions. The previous algorithm only used $O(n)$ memory (one value for each call to `rod_cut`). For this one, it could be the case that the optimal way to cut a rod of any length is into pieces all of length $1$, in which case each cut list will be length $O(n)$ and there are n of them so the storage cost will be $O(n^2 )$. Let’s see if we can do better.



#### Reconstruction

The reason the previous algorithm used so much memory is that it is storing redundant information. The rod cutting problem has optimal substructure, so let’s use that. Let’s say we know that the optimal solution for a rod of length $ n$ is to first make a cut of length$ i$ and sell that, and then do the optimal set of cuts for a rod of length $n − i$. Now let’s say that for each $n$, we store only the value $V_n$ and the first cut length $c_n$. This will take $O(n)$ storage in total since we’re now just storing two values for each cut rather than one, but not as many as $n$ values.

But what good is it to just store one cut? We need to know all the cuts! Well, we can now reconstruct the solution at the end. Given a rod of length $n_1 = n$, we first make a cut $c_n$. This leaves us a rod of length $n_2 = n_1 − c_{n1}$ . Now, we know that the first cut we should make on this rod is $c_{n2}$ leaving us a rod of length $n_3 = n_2 − c_{n2}$ , and so on until we have no rod left. Here’s the code:

```python
def rod_cut_decision(n, p, memo):
	if n not in memo:
		bestprice = 0
		for i in range(1, n+1):
			subprice, nextcut = rod_cut_decision(n-i, p, memo)
			if p[i-1]+subprice>bestprice:
				bestprice = p[i-1]+subprice
				bestcut = i
		memo[n] = (bestprice, bestcut)
	return memo[n]

def rod_cut(n, p):
	# n best price next cut
	memo = {0: (0, 0 ),
			1: (p[0], 1 )}
	bestprice, bestcut = rod_cut_decision(n, p, memo)
	best_cuts = []
	while n:
		subprice, nextcut = memo[n]
		best_cuts.append(nextcut)
		n -= nextcut
	return bestprice, best_cuts
```

Reconstructing the solution at the end could take as much as $O(n)$ time, but since the algorithm already takes $O(n^2 )$ time, this doesn’t change the complexity.



#### Bottom-up approach

So far we have looked at the top down solution, but I said earlier that if possible, it’s better to use a bottom up solution. We know that we end up calculating the best solution for each $i = 1, ... , n$ and that these are ordered, integer arguments, and that to calculate the best solution for $i$ we only need to know the solutions for $j < i$. So we should be able to construct a bottom-up solution. We only need to store the best price and the next cut, which is simple array data. Here’s the code:

```python
def rod_cut(n, p):
	bestprices = zeros(n+1, dtype=int)
	nextcuts = zeros(n+1, dtype=int)
	bestprices[0] = 0
	nextcuts[0] = 0
	bestprices[1] = p[0]
	nextcuts[1] = 1
	for i in range(2, n+1): # i from 2 to n
		for nextcut in range(1, i+1): # from 1 to i
			if bestprices[i-nextcut]+p[nextcut-1]>bestprices[i]:
				bestprices[i] = bestprices[i-nextcut]+p[nextcut-1]
				nextcuts[i] = nextcut
	# reconstruct solution
	bestcuts = []
	bestprice = bestprices[n]
	while n:
		bestcuts.append(nextcuts[n])
		n -= nextcuts[n]
	return bestprice, bestcuts
```
