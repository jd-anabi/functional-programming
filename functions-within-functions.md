[Back to main](https://jd-anabi.github.io/functional-programming/)

In our previous lesson, we learned how to create more complicated functions using if-then-else 
statements and guards. Now, we will go one step further in how we create functions, by composing 
functions.

## Function composition
Recall from math that if we have two functions  
&fnof; : X &rarr; Y and g : Y &rarr; Z,  
then the composistion of these two functions is  
(&fnof; &#8728; g) : X &rarr; Z.  
In other words,  
(&fnof; &#8728; g)(x) = &fnof;(g(x)) &forall; x &isin; X.
