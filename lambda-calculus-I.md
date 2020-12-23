[Back to main](https://jd-anabi.github.io/functional-programming/lambda-calculus-I)

Now that we have a nice grasp on Haskell and functional programming, we will begin to 
switch gears to the more theory side of things. To this end, we will be studying 
lambda calculus.

# Introduction
Formally speaking, lambda calculus is a formal mathematical system for 
expressing computation. It is Turing complete, and it is based around the idea of 
binded variables and substitution. 

Specifically, a lambda expression can be defined as follows:

E := x | &lambda;x. E<sub>1</sub> | E<sub>1</sub> E<sub>2</sub> 

What this means is that a lambda expression can either be a: 
1. A variable (*x*)
2. An abstraction (*&lambda;x.E<sub>1</sub>*, where *E<sub>1</sub>* is also a lambda expression)
2. An application (*E<sub>1</sub> E<sub>2</sub>*, where *E<sub>1</sub>*, *E<sub>2</sub>* are also lambda expressions)

For example, *((&lambda;x.(&lambda;y. x y)) z)* is an expression that is an application between a variable *z* and 
an abstraction *(&lambda;x.(&lambda;y. x y))*. We can drop the parentheses if there is no ambiguity in the expression. 
Thus, we can write the previous lambda expression as *(&lambda;x.&lambda;y. x y) z* without any abiguity.

# Rules
When working with lambda expressions, there are two computation rules that we follow:
1. &alpha;-conversion
2. &beta;-reduction
