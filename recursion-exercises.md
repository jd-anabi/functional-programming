[Back to main](https://jd-anabi.github.io/functional-programming/)

# Subtraction
Design a function that takes in two integers, *p* and *q*, and returns 
the difference *p-q*. Assume that *p-q = 0* if *p &lt; q*. Also, assume 
that *p, q &gte; 0*. For example, *subtr 2 5 = 0*.

## Greater Than
Using your subtraction function, create another function that takes 
in two integers, *p* and *q* such that p, q &gte 0, and returns 
wheter *p* is strictly greater than *q*.

# Logistic Map
The logistic map, as mentioned in a previous post, is given by the 
following equation: 

x<sub>n+1</sub> = rx<sub>n</sub>(1 - x<sub>n</sub>) 

Write a Haskell function that takes in an initial x<sub>0</sub>, 
constant r, and index n to compute x<sub>n+1</sub>.
