[Back to main](https://jd-anabi.github.io/functional-programming/)

In most programming languages, the use of conditionals is very common. For example, 
if we want to choose the smaller number of two numbers, we write the following 
(pseudo-) code:

```haskell
if x < y then x else y
```

If x is less than y, we take the **then** branch. However, if x isn't less than y, we take 
the **else** branch. Also, as we can see, the **if** clause always evaluates a TRUE or FALSE 
statement. Thus, if we want to implement this logic in lambda calculus, we need to do things:
1. We need a way of representing if-then-else logic itself
2. We need a way of representing the booleans TRUE and FALSE

Let's tackle the latter issue first.

# TRUE and FALSE
We can represent TRUE and FALSE in lambda calculus by defining them as follows:

TRUE := &lambda;x.&lambda;y. x
FALSE := &lambda;x.&lambda;y. y

Now, it might not mean much now, but once we have a way of implementing if-then-else logic, 
hopefully it will become more clear.

# If-Then-Else
Now, if-then-else takes in three arguments:
1. A boolean expression in the **if** clause
2. A statement in the **then** clause
3. A statement in the **else** clause

Thus, we can represent if-then-else in lambda calculus by using a abstraction with three binders as follows:

IF-THEN-ELSE := &lambda;x.&lambda;y.&lambda;z. x y z

This seems like a fairly standard abstraction with three binders, so how could this possibily give us our 
desired logic? Well, let's combine it with our definitions of TRUE and FALSE

(1) (&lambda;x.&lambda;y.&lambda;z. x y z) (&lambda;x.&lambda;y. x) p q
(2) (&lambda;x.&lambda;y.&lambda;z. x y z) (&lambda;x.&lambda;y. y) p q

Now, the first statement represents 
```haskell
if TRUE then p else q
```

Let's use our beta-reduction rules to see how this is the case.

(&lambda;x.&lambda;y.&lambda;z. x y z) (&lambda;x.&lambda;y. x) p q

&rarr; (&lambda;y.&lambda;z. (&lambda;x.&lambda;y. x) y z)  p q

&rarr; (&lambda;z. (&lambda;x.&lambda;y. x) p z) q

&rarr; (&lambda;x.&lambda;y. x) p q

&rarr; (&lambda;y. p) q

&rarr; p

As we can see, we take the **then** branch because our boolean expression in the **if** clause is TRUE. The 
same can be done for the second statement.

(&lambda;x.&lambda;y.&lambda;z. x y z) (&lambda;x.&lambda;y. y) p q
&rarr; (&lambda;y.&lambda;z. (&lambda;x.&lambda;y. y) y z)  p q
&rarr; (&lambda;z. (&lambda;x.&lambda;y. y) p z) q
&rarr; (&lambda;x.&lambda;y. y) p q
&rarr; (&lambda;y. y) q
&rarr; q
