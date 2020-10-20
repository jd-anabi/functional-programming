[Back to main](https://jd-anabi.github.io/functional-programming/)  

Before we get started in Haskell, it is imperative (I know, I'm very funny) to understand the differences between
an imperative programming language and a functional one.

# **Imperative Programming**
If I ask you what programming is, you might say that it is the process of designing sequential steps, that a computer 
follows, which alter the state of the program.  

For example, say you wanted to computer the sum of the integers between
1 and n, inclusively (i.e. 1 + 2 + 3 + ... + n). We could write a simple program that does this for us. In Python, it would
look something like this:
```python
sum = 0
for x in range(1, n+1):
    sum = sum + x
```
As we can see, the computer is just following a specified amount of sequential steps. It starts at *sum = 0*. Then it moves
to the next line, where it sets *x = 0*. Then it moves to the next line where it computes *sum = 0 + 1* before setting *x = 1*
and doing the process over again. Each line acts like a sequential step, in which the state of the program is altered each time.  

This way of programming is perfectly valid. However, there is another type of programming paradigm known as functional programming.

# **Functional Programming**
Functional programming, on the other hand, is based on function construnction, composition, and application. That is, our program is
designed around functions, and how we compose them and apply them. For example, in Haskell, if we wanted to compute the same sum as 
mentioned before, we would write:
```haskell
sum_n :: Int -> Int
sum_n 0 = 0
sum_n n = n + sum (n-1)
```
Now it is ok if you don't completely understand the syntax right now. But what this basically says is that we a function sum, with an
argument N, that we have defined in a recursive manner. Mathematically, it looks something like this:  

sum(0) = 0  
sum(n) = n + sum (n-1)  

If you are still confused, it's ok, we will show a simple example for n = 5 that will hopefully make it more clear.  

sum(5) =  
5 + sum(4) =  
5 + 4 + sum(3) =  
5 + 4 + 3 + sum(2) =  
5 + 4 + 3 + 2 + sum(1) =  
5 + 4 + 3 + 2 + 1 + sum(0) =  
5 + 4 + 3 + 2 + 1 + 0 =  
15  

The jist of this is that the programming is not following a set of sequential statements. Rather, the program is determined by how we define, 
compose, and apply our functions. However, the way we define our functions in Haskell is through [recursion](https://jd-anabi.github.io/functional-programming/recursion).
