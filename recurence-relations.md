[Back to main](https://jd-anabi.github.io/functional-programming/)  

# Reccurence Relations
To understand functions in Haskell, it is necessary to understand reccurrence relations. 
Reccurence relations are functions that are defined in terms of themselves. To understand this, 
we will do multiple examples.

## Examples
### Summing from 0 to N, where N is a non-negative integer
S(0) = 0  
S(N) = N + S(N-1)
### Factorial of N
0! = 1  
N! = N * (N-1)!
### Fibonacci Sequence
F(0) = 0  
F(1) = 1  
F(N) = F(N-1) + F(N-2)
### Logistic Map (given a constant r and initial x<sub>0</sub>)
x<sub>n+1</sub> = rx<sub>n</sub>(1 - x<sub>n</sub>)  

Hopefully now you are more comfortable with recursion and reccurrence relations.
