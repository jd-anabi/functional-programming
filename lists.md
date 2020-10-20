[Back to main](https://jd-anabi.github.io/functional-programming/)  

Now that we know how functions work in Haskell, let's try some applications with them using lists.  

## Working with lists
Before we make functions with lists, we should learn how they work in Haskell.  
### Constructing Lists
A list can be constructed in the following manner:
```Haskell
[]
```
is the empty list in Haskell.
```Haskell
x:xs
```
is a list with x as its first element, which continues with xs. An example would be:  
[1,2,3] = 1:[2,3] = 1:(2:[3]) = 1:(2:(3:[]))  
If you look closely, you can see how recursion is inherent to the structure of a list. 
In more mathematical notation:  
X<sub>x<sub>0</sub>,x<sub>n</sub></sub> = A(x<sub>0</sub>, X<sub>x<sub>1</sub>,x<sub>n</sub></sub>),  
where 
X<sub>x<sub>0</sub>,x<sub>n</sub></sub> is a list X starting with element x<sub>0</sub> and 
running up to element x<sub>n</sub>, A(y<sub>p</sub>, Y) is a function that appends the element y<sub>p</sub> to the front of list Y.  
### Deconstructing Lists
A list can be deconstructured in the following manner:
```Haskell
head(x:xs) = x
tail(x:xs) = xs
```
All of this should give us a solid basis for working with lists.

## Examples
Now that we know how to make functions and lists, we can do some pretty neat things.
### Length
We can compute the length of a list by doing the following:
```Haskell
len :: List -> Int
len [] = 0
len x:xs = 1 + (len xs)
```
For example, suppose we have the list [1,2,3]. Then,  
len [1,2,3]  
= 1 + (len [2,3])  
= 1 + 2 + (len [3])  
= 1 + 1 + 1 + (len [])  
= 1 + 1 + 1 + 0  
= 3  
### End Append
We can append an element y to the end of a list x:xs by doing the following:
```Haskell
end_append :: List -> Int -> List
end_append [] y = y:[]
end_append (x:xs) y = x : (end_append xs y)
```
For example, let's take the list [1,2,3] and append 4 to the end of it:  
end_append [1,2,3] 4  
= 1:(end_append [2,3] 4)  
= 1:(2:(end_append [3] 4))  
= 1:(2:(3:(end_append [] 4)))  
= 1:(2:(3:(4:[])))  
= [1,2,3,4]  

These are just a couple of examples that we could have down. Check the Haskell Exercises section for more examples.
