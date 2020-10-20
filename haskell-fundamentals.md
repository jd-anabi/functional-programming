[Back to main](https://jd-anabi.github.io/functional-programming/)

If you have installed Haskell, we are ready to begin learning the basics. If not, 
please go [here](https://www.haskell.org/platform/) to install it.  

# Functions
One of the most fundamental aspects of Haskell is functions. Learning how to create, compose, and apply functions is essential to working with Haskell. 
Whenever you are write a function, it will usually follow the basic format (the ... indicate that this code wouldn't actually run; it is merely for demonstration purposes):  
```Haskell
f :: at1 -> at2 -> ... -> atn -> rt  
f O1 O2 ... On = br  
f a1 a2 ... an = r 
```
where  
* f is the name of the function
* {at1,at2,...,atn} are the types of the arguments
* rt is the type of the return value
* {O1,O2,...,On} are the argument values of the base case
* br is the return value of the base case
* {a1,a2,...,an} are the values of the non-base case arguments
* r is the return value of the non-base case
If you understand this, we are ready to go over some examples.

# Examples
Let's try to write a Haskell function that computes the nth fibonacci number.  
Firstly, let's write the recurrence relation of the fibonacci sequence:  
fib(0) = 0  
fib(1) = 1  
fib(n) = fib(n-1) + fib(n-2)  
This can be easily converted into Haskell like:  
```Haskell
fib :: Int -> Int
fib 0 = 0
fib 1 = 1
fib n = (fib n-1) + (fib n-2)
```
As we can see, this is a clear corrollary between the mathematical reccurence relation and the recursive Haskell function.  
If you are still not comfortable with this, see the [recurence relations](https://jd-anabi.github.io/functional-programming/recurrence-relations) 
section for more help. If you are comfortable with these recurrence relations, we are ready  to work with [lists in Haskell](https://jd-anabi.github.io/functional-programming/).
