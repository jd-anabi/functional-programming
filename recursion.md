[Back to main](https://jd-anabi.github.io/functional-programming/)  

From the last tutorial, you might have noticed that when we defining our function for sum, we used recursion.
Indeed, any non-trivial function in Haskell is recursive by nature since Haskell does not provide any
mechanism for looping, like for-loops or while-loops that are present in other languages. This, then, 
brings us to our next topic: recursion.  

# **What is recursion**
Recursion, simply put, is defining something in terms of itself. Thus, a recursive function is a function
that is defined in terms of itself. A very popular example that helps in demonstrating this is through 
the use of the factorial function. Mathematically, one can define the factorial of n as a recurrence relation:  

n! = n * (n-1)!  
For example:  
5! = 5 * 4! = 5 * 4 * 3! = 5 * 4 * 3 * 2! = 5 * 4 * 3 * 2 * 1! = 5 * 4 * 3 * 2 * 1 * 0! = 5 * 4 * 3 * 2 * 1 * 1 = 120  

In Python, we can define this as the function:  
```python
def factorial(n):
    if n = 0:
        return 1
    return n * factorial(n-1)
```  
For n = 5, this would be:  
fact(5) = 5 * fact(4) = 5 * 4 * fact(3) = 5 * 4 * 3 * fact(2) = 5 * 4 * 3 * 2 * fact(1) = 5 * 4 * 3 * 2 * 1 * fact(0) = 5 * 4 * 3 * 2 * 1 * 1 = 120  
This agrees with our previous mathematical recurrence relation.  

If you understand all of this, then you are ready to start learning the [basics of Haskell](https://jd-anabi.github.io/functional-programming/haskell-funcdamentals).
