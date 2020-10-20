[Back to main](https://jd-anabi.github.io/functional-programming/)  

In the previous two sections, we covered the basic of functions in Haskell. Now we will see 
how to construct more sophisticated functions, and to do this, we will first take a look at 
our mathematical friend, the piecewise function.

## The Piecewise Function
In math, you might have encountered what is known as a piecewise function. For example, the 
following  
&fnof;(x) = { x&sup2; if x &gt; 0, 0 otherwise  
says that **if** x &gt; 0 **then** &fnof;(x) = x&sup2; **else** &fnof;(x) = 0.  
I highlight the if then and else because Haskell has what are known as 
if-then-else statements. Let's see how they work.

## If-then-else
Basically, a Haskell if-then-else statement is constructed using the following format:
```Haskell
if --condition
    then --do A
    else --do B
```
