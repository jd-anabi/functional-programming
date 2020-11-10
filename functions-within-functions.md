[Back to main](https://jd-anabi.github.io/functional-programming/)

In our previous lesson, we learned how to create more complicated functions using if-then-else 
statements and guards. Now, we will go one step further in how we create functions, by composing 
functions.

## Function composition
Recall from math that if we have two functions &fnof; : X &rarr; Y and g : Y &rarr; Z, 
then the composistion of these two functions is (&fnof; &#8728; g) : X &rarr; Z. This 
reads as a map from elements x &isin; X to elements g(x) &isin; Z. In other words, 
(&fnof; &#8728; g)(x) = &fnof;(g(x)) &forall; x &isin; X.  
  
This notion of function composition can be readily extended to Haskell, as we shall see.

## Function composition examples
Before we begin working with this idea of function composition within Haskell, it is important 
to understand why should care about something like this; for motivation, we shall look at a 
physical example of functions being composed together.

### Physics
#### Lagragian
In physics, one often works with what is known as the Lagragian. For a simple pendelum 
of mass m and length l, the Lagragian can be written as:  
L = L(&phi;(t), <sup>d</sup>&frasl;<sub>dt</sub>(&phi;(t))) = (&frac12;)ml(<sup>d</sup>&frasl;<sub>dt</sub>(&phi;(t)))<sup>2</sup> - mgl(1 - cos(&theta;))  
Now, you don't need to know what the Lagragian is. But notice how it can be seen as a 
function composed of of other functions. Hopefully, this motivates us in our desire to 
translate our mathematical knowledge of function composition to Haskell.

## Functions within Functions within Functions within ... within Functions within Haskell
Now that we have a mathametical framework of composing functions together, let's see how 
we can do something similar in Haskell. For example, say we wanted to write a function for 
what we did above for &fnof;(g(x)), assuming that &fnof;(g(x)) = g(x)<sup>2</sup>; in Haskell, 
it would look something like this (let's just assume for now that x, g(x), &isin; &#8484;):
```haskell
f :: (Int -> Int) -> Int -> Int
f g x = (g x) * (g x) 
```
Now let's examine this code.  
Our function f takes in two arguments: one of type (Int -> Int) and another of type Int. The second 
argument is simply just an integer, but the first argument might seem a little strange at first. 
(Int -> Int) is simply a function that takes in an integer and returns an integer. Thus, the two 
arguments of our function f are another function, say g, and an integer, say x. However, there 
is one subtle difference between how functions are composed in Haskell compared to how they are 
defined mathematically. Notice in Haskell, that our function has an explicit dependence on x. 
Mathematically, this doesn't have to always be the case. Notice with our Lagragian, there is 
explicit dependence on &phi; and <sup>d</sup>&frasl;<sub>dt</sub>(&phi;(t)), but not on t. If 
we were to write this in Haskell, the arument types would look something like this:
```haskell
L :: (Int -> Int) -> (Int -> Int) -> Int -> Int
```
Now that we have a basis for function composition in Haskell, what can we actually do with it? Well, let's 
take a look at some examples for motivation.

## Haskell function composition examples
### Returning the odd elements in a list
```haskell
-- determines if some number n is even
is_even :: Int -> Bool
is_even n = n `rem` 2 == 0

-- returns a list that contains only the even elements of input list
even_list :: (Int -> Bool) -> [Int] -> [Int]
even_list f [] = []
even_list f (x:xs)
    | f x = x : (even_list f xs)
    | otherwise = (even_list f xs)
```
For example, to determine the even elements of the list [1,2,7,10,15], we would run: 
```haskell
even_list is_even [1,2,7,10,15]
```
This returns the list [2,10] as expected. Let's go through this example step-by-step. 
```haskell
even_list is_even [1,2,7,10,15]
= even_list is_even [2,7,10,15] # since 1 `rem` 2 =\= 0
= 2 : (even_list [7,10,15]) # since 2 `rem` 2 = 0
= 2 : (even_list [10,15]) # since 7 `rem` 2 =\= 0
= 2 : (10 : (even_list [15])) # since 10 `rem` 2 = 0
= 2 : (10 : (even_list []))) # since 15 `rem` 2 =\= 0
= 2 : (10 : ([])) # by our base case
= [2,10]
```
 
Now that we have a good understanding of function composition, I suggest taking a look at the exercises. Once you are comfortable with everything we have learned so far, we can begin to learn about [modules](https://jd-anabi.github.io/functional-programming/modules).
