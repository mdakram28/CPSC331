# Session 01: Mathematical Induction

#### Email: mohdakram.ansari@ucalgary.ca
#### Tutorials:
- T01 (12:00 - 2:00 PM)
- T02 (2:00 - 4:00 PM)

---

## Agenda

1. Mathematical Induction, strong and week
2. Loop Invariants

---
## 1. Mathematical Induction (Weak)

- Suppose you want to prove that a statement about an integer n is true for every positive integer n.
- Define a propositional function P(n) that describes the statement to be proven about n.
- To prove that P(n) is true for all n ≥ 1, do the following two steps:
    - **Basis Step**: Prove that P(1) is true.
    - **Inductive Step**: Let k ≥ 1. Assume P(k) is true, and prove that P(k + 1) is true.

### Example: 
Prove that algorithm f(n) returns n! for all nonnegative integers n ≥ 0.

**Procedure:**
```
f(n: nonnegative integer)
    if (n = 0) then return 1
    else return n*f(n − 1)
```

Given:
- f(n) = n! 

Prove That:
- f(n+1) = (n+1)!

Proof:
- f(n) = n! 
- f(n) = n * (n-1) * (n-2) * ... * 1
- **(n+1)** * f(n) = **(n+1)** * n * (n-1) * (n-2) * ... * 1
- f(n+1) = (n+1) * n * (n-1) * (n-2) * ... * 1
- f(n+1) = (n+1)!

### Strong Induction
- To prove that P(n) is true for all n ≥ 1, do the following two steps:
    - Basis Step: Prove that P(1) is true.
    - Inductive Step: Let k ≥ 1. Assume P(1), P(2), . . . , P(k) are all true, and prove that P(k + 1) is true.

### Example:
Every positive integer greater than 1 can be written as a prime or as the product of two or more primes.

**Proof:**

Consider P(n) the statement “n can be written as a prime or as the product of two or more primes.”. We will use strong induction to show that P(n) is true for every integer n ≥ 1.

Basis Step: P(2) is true, since 2 can be written as a prime, itself.

Induction Step: Let k ≥ 2. Assume P(1), P(2), . . . , P(k) are true. We will prove that P(k + 1) is true, i.e. that k + 1 can be written as a prime or the product of two or more primes.
1. **Case 1: k + 1 is prime.** If k + 1 is prime, then the statement is true as k + 1 can be written as
itself, a prime.
2. **Case 2: k + 1 is composite.** By definition, there exist two positive integers a and b with $2 ≤ a ≤ b < k + 1$, such that $k + 1 = ab$. Since $a, b < k + 1$, we know by induction hypothesis that a and b can each be written as a prime or the product of two or more primes. Thus, $k + 1 = ab$ can be written as a product of two or more primes, namely those primes in the prime factorization of a and those in the prime factorization of b. 


## 2. Loop Invariants


Algorithm using loop:
1. **Initialization**
2. **Loop**
3. **Output**

### Example:
Procedure: 
```
LogRounded(x: integer): integer
    i ← 0
    y ← 1
    IF x ≤ 0 then Return “error”
    While y < x do:
        i ← i + 1
        y ← 2 ∗ y
    Return i
```

**Proof:**

Loop Invariant: After the t’th iteration, $y = 2^i$

Base Case: After 0 iterations (t=0), y = 1 and i = 0

Induction: 
- $y_B$, $i_B$ : Value of y and i after t'th iteration (Before t+1'st iteration)
- $y_A$, $i_A$ : Value of y and i after t+1'st iteration.
- Assume, $y_B = 2^{i_B}$ holds before the (t+1)'st iteration.
- After (t+1) iteration:
    - Let, $y_A =  2{y_B}$
    - Let, $i_A = i_B + 1$
    - $y_A =  2*y_B$
    - $y_A = 2*2^{i_B}$
    - $y_A = 2^{i_B+1}$
    - $y_A = 2^{i_A}$
    - Thus the invariant is proved at the end of t+1'st iteration

**Proving correctness**

Let t be the last iteration, where
the guard fails.

- $y_B < x \le y_A$
- Since, $y_A = 2y_B$, 
- $y_B < x \le 2y_B$
- $2^i < x \le 2*2^{i}$
- $2^i < x \le 2^{i+1}$
- $i < log_2(x) \le i+1$

Thus, $i_A$ is the closest integer greater
than $log_2(x)$

