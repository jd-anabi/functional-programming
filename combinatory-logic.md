[Back to main](https://jd-anabi.github.io/functional-programming/)

Combinatory logic, like lambda calculus, is a theoretical framework to represent computation. 
Again, like lambda calculus, this model of computation is Turing complete. However, unlike 
lambda calculus, combinatory logic removes the need for abstraction, which makes it a simpler, 
but just as powerful, model of computation. 

# Introduction
Just like lambda calculus, a combinatory term can take three of the following forms:

E := x | P | (E<sub>1</sub> E<sub>2</sub>)

That is, a combinatory terms can either be a:
1. A variable (x)
2. A priminitive function (P)
3. An application ((E<sub>1</sub> E<sub>2</sub>))

Now, a variable is just some character that represents a combinatory term. However, the primitive functions are 
bit more interesting. However, before discussing that, I would just like to mention that to make notation simple, 
we will drop parantheses when appropiate. Take note, however, that we will be using the convention of left-associativity. 
That is,

E<sub>1</sub> E<sub>2</sub> E<sub>3</sub> E<sub>4</sub>

is equivalent to

(((E<sub>1</sub> E<sub>2</sub>) E<sub>3</sub>) E<sub>4</sub>)

# Primitive Functions
A primtive function can be either one of the three combinatory symbols **I**, **K**, or **S**. These symbols are 
defined as follows.

## I
**I** is the identity combinator such that 

(**I** x) = x 

&forall; terms x

## K
**K** is the constant combinator which creates constant functions. That is, (**K** x) is the function that 
returns x for any argument y. Formally, this reads as

((**K** x) y) = x

Dropping parantheses, this reads as

**K** x y = x

## S
**S** is the combinator which generalizes application by first applying z to x and y, before applying y to x. Formally this 
reads as

**S** x y z = x z (y z)

## Revisiting I
Notice however, that the combinator **I** can just be written in terms of the combinators **K** and **S** 

**S** **K** **K** x

= **K** x (**K** x)

= x

Thus, the use of the **I** combinator is just for convience.

However, this is just scracthing the surface of combinatory logic. If you would like to learn more about it, 
I suggest taking a look at the suggested readings section.
