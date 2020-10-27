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
of mass m and length L, the Lagragian can be written as:  
&Lscr; = &Lscr;(&phi;(t), <sup>d</sup>&frasl;<sub>dt</sub>(&phi;(t))) = (&frac12;)mL(<sup>d</sup>&frasl;<sub>dt</sub>(&phi;(t)))<sup>2</sup> - mgL(1 - cos(&theta;))  
Now, you don't need to know what the Lagragian is. But notice how it can be seen as a 
function composed of of other functions.  
  
Now that we hopefully have some motivation for composing functions, let's move onto to working in Haskell.

## Functions within Functions within Functions within ... within Functions within Haskell
