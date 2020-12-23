[Back to main](https://jd-anabi.github.io/functional-programming/)

If you have worked in other programming languages, you are probably familar with the 
concept of modules. For example, in Java, a package organizes java classes into namespaces. 
The same idea can be applied to Haskell. In Haskell, a program can be thought of as a 
collection of modules. Like java, modules serve the purpose for creating namespaces, but 
they also create abstract data types (if you would like to learn more about ADTs, I recommend 
starting [here](https://wiki.haskell.org/Abstract_data_type)). 

# Creating a Module
We can create a module by using the keyword *module*. For example, suppose we want to create a 
module that contains a function that computes the binomial coefficients 
(click [here](https://en.wikipedia.org/wiki/Binomial_coefficient) if you'd like to learn more 
about binomial coefficients).

```haskell
module Binomial (fac, choose) where

fac :: Int -> Int
fac 0 = 1
fac n = n * fac (n-1)

choose :: Int -> Int -> Int
choose n m = (fac n) `div` ((fac m) * (fac (n-m)))
```
Now we can import this module into another one of our programs.

# Importing a Module
We can import our previous module by using the *import* keyword.

```haskell
module Main (main) where
import Binomial

main = print (choose 5 2)
```

If you are having trouble loading the module, you might need to use *:set -v* in ghci.

# Other Useful Modules
## Set Module
If you are unfamilar we the concept of a set, that is ok. In mathematics, a set is an unordered, 
collection of distinct elements. In Haskell, we can use sets by importing the module *Data.Set*. 
In the following example we will compute the union of two sets.

```haskell
-- qualified keyword needed for ghci
import qualified Data.Set as Set

s1 = Set.singleton 1
s2 = Set.singleton 3
s3 = Set.union s1 s2

insert_function_example = Set.insert 2 s3
```

If you would like to learn about sets, I recommend starting [here](https://hackage.haskell.org/package/containers-0.6.4.1/docs/Data-Set.html). 
There are also many other modules that are useful such as [list](https://hackage.haskell.org/package/base-4.14.1.0/docs/Data-List.html) 
and [maps](https://hackage.haskell.org/package/containers-0.6.2.1/docs/Data-Map.html). 

Now that we have learned about modules, we can learn about [monads](https://jd-anabi.github.io/functional-programming/monads-I).
