[Back to main](https://jd-anabi.github.io/functional-programming/)

As we discussed in our previous post, there are two ways to go about implementing 
De Bruijn indices: either through pure or mixed indices. I would like to focus our 
attention on mixed indices, and outline a algorithmic draft of implementing them in Haskell. 

# Outline of Algorithm
The following (pseudo-) code represents a rough outline on how to go about implementing 
this mixed index notation in Haskell.

```haskell
deBruijn (EAbs x e) = 
    write "\" -- use I/O monad
    push x on the stack -- use state monad
    deBruijn (e)
    pop x off the stack

deBruijn (EVar x) = 
    compute the index of x by finding its position on the stack
    write index -- use I/O monad

deBruijn (EApp e1 e2) = 
    write (deBruijn e1) ++ write (deBruijn e2)
```
