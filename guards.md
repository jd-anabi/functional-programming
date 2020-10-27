[Back to main](https://jd-anabi.github.io/functional-programming/)  

In the previous two sections, we covered the basic of functions in Haskell. Now we will see 
how to construct more sophisticated functions, and to do this, we will first take a look at 
our mathematical friend, the piecewise function.

## The Piecewise Function
In math, you might have encountered what is known as a piecewise function. For example, the 
following  
<img src="https://github.com/jd-anabi/functional-programming/blob/gh-pages/equations/piecewise.png" width="48">
says that **if** |x| &gt; 1 **then** &fnof;(x) = x&sup2; **else** &fnof;(x) = 0.  
I highlight the if then and else because Haskell has what are known as 
if-then-else statements. Let's see how they work.

## If-then-else
Basically, a Haskell if-then-else statement is constructed using the following format:
```haskell
if --condition
    then --perform A
    else --perform B
```
where A and B are arbitrary operations. To get a more concrete understanding of this, let's 
try to construct our aformentioned piecewise function in Haskell.
```haskell
f :: Int -> Int
f x = 
    if abs (x) > 1
        then x*x
        else 0
```
Looking at this code, we can see that **if** |x| &gt; 1, **then** our function returns x&sup2; **else** it returns 0. 
This has the same logic as our piecewise function. However, Haskell does provide another, perhaps more elegant, way 
of doing the same thing; this is what is known as guards.

## Guards
The basic structure of guards is constructed as follows:
```haskell
f x
    | condition 1 = A1
    | condition 2 = A2
    .
    .
    .
    | condition n = An
```
where Ap is some arbitrary operation &forall; p &isin; {1, 2, ... n}.  
Looking at this structure, it seems like guards allows more flexibility when compared to our aformentioned if-then-else 
statement. And that is true. Guards can do the same things as if-then-else statements, but more elegantly (in my opinion).  
To get a concrete understanding of guards, let's construct our piecewise function using them.
```haskell
f :: Int -> Int
f x
    | abs(x) > 1 = x*x
    | otherwise = 0
```
Now, this looks similar to our if-then-else construction from before. But you might have notice the **otherwise** statment. 
The otherwise statement is simply always true, and it serves a similar purpose as the otherwise in our piecewise function. 
Basically, if all the conditions before the otherwise evaluate to false, then the expression for the otherwise statement is
evaluated and returned.  

Now that we have a basic understanding of constructing more complicated Haskell functions, I suggest taking a look at the 
Haskell Exercises section to test your understanding. When you feel comfortable enough with everything we have discussed, 
then we can work on ways to construct [more complicated functions](https://jd-anabi.github.io/functional-programming/functions-wthin-functions).
