# Session 01: 

## Email: mohdakram.ansari@ucalgary.ca

## Agenda

1. Math Induction, strong and week
2. Loop Invariants



---
## 1. Math Induction

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

$$
\text{Given: } f(n) = n*(n-1)*(n-2)*...*1
\\
(n+1) * f(n) = (n+1)*n*(n-1)*(n-2)*...*1
f(n+1) = (n+1)*n*(n-1)*(n-2)*...*1
$$