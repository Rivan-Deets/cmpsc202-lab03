# Lab 3: Asymptotic Analysis

This lab focuses on understanding and analyzing the asymptotic behavior of algorithms. We will explore concepts such as Big-O, Big-$\Theta$, and Big-$\Omega$ notations, and apply them to various algorithmic problems to determine their efficiency and scalability.

**Instructions:** To complete this lab, you may work in groups, but you must write your solutions yourself. Once you have completed the lab, push your changes to your forked repository.

## Problem 1

Suppose $T(n)$ is the worst case running time of an algorithm with input size $n$, and we know that $T(n)$ is $\mathcal{O}(n^3)$ and $\Omega(n^2)$. For each of the following statements, determine whether it must be true, must be false, or could be either true or false. Give a brief justification for each. 

1. $T(n)$ is $\mathcal{O}(n^2)$.
    **Could be either true or false.** If $T(n)=n^2$, this is true. If $T(n)=n^3$, it is false. Both examples satisfy the given bounds.

2. $T(n)$ is $\Theta(n^3)$.
    **Could be either true or false.** If $T(n)=n^3$, this is true. If $T(n)=n^2$, it is false. Both examples satisfy the given bounds.

3. $T(n)$ is $\Omega(n)$.
    **Must be true.** If $T(n)$ grows at least as fast as $n^2$, it also grows at least as fast as $n$.

4. $T(n)$ is $\Theta(n^{1.5})$.
    **Must be false.** This would mean $T(n)$ grows like $n^{1.5}$, slower than the given lower bound of $n^2$.
    '
5. $T(n)$ is $\mathcal{O}(n)$.

    **Must be false.** This would mean $T(n)$ grows no faster than $n$, which conflicts with the given lower bound of $n^2$.

6. $T(n)$ is $\Theta(n^2 \log n)$.
    **Could be either true or false.** $n^2\log n$ grows between $n^2$ and $n^3$, so it is one possible growth rate. Other rates, such as $n^2$, also satisfy the given bounds.


## Problem 2
Consider the following algorithm where $f(A, i, j)$ is an unknown algorithm that takes as input an array $A$ and two indicies $i$ and $j$ and returns a number. 

```
Mystery Algorithm
Input: An array of int $A$ of length $n$.
Output: int sum
    n = |A|
    sum = 0
    for i = 1 to n:
        for j = 1 to n:
            sum += f(A, i, j)
```

Without knowing anything about $f$, what can we say about the running time of the Mystery Algorithm in terms of $n$? Justify your answer. 

The outer loop runs $n$ times, and the inner loop runs $n$ times for each outer-loop iteration. Therefore, the algorithm calls $f$ exactly $n^2$ times.

Without knowing how long each call to $f$ takes, we cannot determine the Mystery Algorithm's total running time in terms of $n$ alone. If each call to $f$ takes $g(n)$ time, the total running time is $\Theta(n^2 g(n) + n^2)$, including the loops' overhead. For example, if each call takes constant time, the Mystery Algorithm runs in $\Theta(n^2)$ time.
