[Back to main](https://jd-anabi.github.io/functional-programming/)

As we discussed in our previous post, there are two ways to go about implementing 
De Bruijn indices: either through pure or mixed indices. I would like to focus our 
attention on mixed indices, and outline a algorithmic draft of implementing them in Haskell. 

# Outline of Algorithm
The following (pseudo-) code represents a rough outline on how to go about implementing 
this mixed index notation in Haskell [NOTE: We are using \ to represent &lambda;].

```haskell
deBruijn (EAbs x e) = 
    write '(\' -- use I/O monad
    push x on the stack -- use state monad
    deBruijn (e)
    pop x off the stack
    write ')'

deBruijn (EVar x) = 
    if x is on the stack
    then compute x's index by finding its position on the stack and write index
    else write x

deBruijn (EApp e1 e2) = 
    write (deBruijn e1) +++ write (deBruijn e2)
```

Let's look at an example and see if this algorithm holds up.

deBruijn (((\x.\y. x y) p) (\z. z))

= write (deBruijn (((\x.\y. x y) p)) +++ write (deBruijn (\z. z))

= write (deBruijn ((\x.\y. x y)) +++ write (deBruijn (p)) +++ write (deBruijn (\z.. z))

= '\' +++ deBruijn (\y. x y) +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '\' +++ '\' +++ deBruijn (x y) +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '\' +++ '\' +++ write (deBruijn x) +++ write (deBruijn y) +++ write (deBruijn (p)) ++ write (deBruijn (\z. z))

= '\' +++ '\' +++ write (2) +++ write (deBruijn y) +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '\' +++ '\' +++ '2' +++ write (deBruijn y) +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '\' +++ '\' +++ '2' +++ write (1) +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '(\' +++ '\' +++ '2' +++ '1' +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ write (deBruijn (p)) +++ write (deBruijn (\z. z))

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ write (p) +++ write (deBruijn (\z. z))

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ 'p' +++ write (deBruijn (\z. z))

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ 'p' +++ '(\' +++ write (z)

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ 'p' +++ '(\' +++ write (1)

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ 'p'+++++ '(\' +++ '1'

= '(\' +++ '\' +++ '2' +++ '1' +++ ')' +++ ')' +++ 'p' +++ '(\' +++ '1' +++ ')'

= '(\ \ 2 1) p (\ 1)'

Thus, this gives us the correct expression in mixed De Bruijn indices. However, lambda calculus isn't the only way to represent 
computation. There is also [combinatory logic](https://jd-anabi.github.io/functional-programming/combinatory-logic).
