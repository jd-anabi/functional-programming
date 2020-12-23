[Back to main](https://jd-anabi.github.io/functional-programming/)

In a few blog posts ago, we mentioned De Bruijn indices, in regards to 
alpha-conversion. Specifically, we saids that if we use De Bruijn indices 
in our lambda expressions, then we don't have to deal with alpha-conversion. 
This is useful because it becomes much easier to see how to expressions 
are logically equivalent. For example, suppose we have two expressions: 

(&lambda;x.&lambda;y.&lambda;z.&lambda;w. x w x z w y)

(&lambda;a.&lambda;b.&lambda;c.&lambda;d, a d a c d b)

Now, it might not be immediately clear, but these two expressions are logically 
equivalent. In De Bruijn indices, however, both these statements are:

(&lambda; &lambda; &lambda; &lambda; 1 4 1 3 4 2)

Thus, this notation is very handy for highlighting the logical equivalence of two expressions. 
It might seem confusing right now, so don't worry. We will start covering the basics right now.

# Introduction
Now, converting an expression to De Bruijn notation, we need to convert, seperately, bounded variables and free variables.

# Bounded variables
When converting bounded variables, we see how many binders are between that variable and its own binder (including that binder itself). 
For example, 

(&lambda;x.&lambda;y. x y x)

becomes

(&lambda; &lambda; 2 1 2)

as the number of binders between x and its own binder is 2 (again, we are also considering x's binder itself). Similary, for y, 
there is 1 binder. 
Note, how in the new notation, there is no need to label our binders anymore. This is due the nature of De Bruijn indices themselves, 
as it becomes clear which binder each index corresponds to. Things are a little different for free variables.

# Free variables
There are two ways we can go about free variables in De Bruijn notation. We can either convert them (pure indices) or 
we can simply leave them as is (mixed indices).

## Pure Indices
Now if we want pure indices, then we first convert all of the bounded variables as mentioned above. Then, we assign each free variable 
a number, making sure that the number is strictly greater than the highest bounded index. For example, 

(&lambda;x.&lambda;y. x y z) u v

becomes 

(&lambda; &lambdal 2 1 3) 4 5

As we can see, z, u, v are free variables, and thus remain strictly greater than bounded variables. 
This discussion of indices, however, begs the following question: how do we perform beta-reduction? 
The idea of beta-reduction fundamentally remains the same, however, this time, we must take care to decrement 
our free variables accordingly. Let's consider our last example:

(&lambda; &lambdal 2 1 3) 4 5

&rarr; (&lambda; 4 1 3) 5

&rarr; (&lambda; 3 1 2) 4

&rarr; 3 4 2

&rarr; 2 3 1

However, this another way of going about De Bruijn indices, which is instead opting for mixed indices. 

## Mixed Indices
When using mixed indices, we leave our free variables as is. The reason for this is two-fold:

1. It should be easier to implement as we do not need to deal with decrementing
2. It should have better performance as, again, we do not need to deal with decrementing 

The reason for the second point is that this need to decrement can get really out of hand for sufficiently long lambda expressions. 
So for example, in the mixed notation our previous lambda expression 

(&lambda;x.&lambda;y. x y z) u v

becomes

(&lambda; &lambda; 2 1 z) u v

Now that we are familar with De Bruijn indices, let's describe an [algorithmic approach for implementing this mixed notation](https://jd-anabi.github.io/functional-programming/algorithmic-de-bruijn).
