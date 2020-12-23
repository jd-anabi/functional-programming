[Back to main](https://jd-anabi.github.io/functional-programming/)

A monad in Haskell is basically a type class that must follow the three Monad Laws:

1. Left identity
2. Right identity
3. Associativity

To understand these rules, let's look at the common Monad class, which all other Monads are derived from.

```haskell
class Monad m where
  (>>=)  :: m a -> (  a -> m b) -> m b
  (>>)   :: m a ->  m b         -> m b
  return ::   a                 -> m a
  fail   :: String -> m a
```

The first two laws state that the return does not change the value and it doesn't change anything thing in the 
monad. Now, what do we mean by return. Well, a monad has the ability to describe a computation that creates a 
Haskell value. This creation is what we mean by return. Formally, the first and second laws can be written as follows:

1. return a >>= f &equiv; f a
2. m >>= return &equiv; m

Now, this notation might seem strange, but if we observe the common monad class, we can see that the first two laws 
are saying that the return should just have the behavior of the identity element on both left and right side= of the 
binding operator >>-.

The third law can be formally written as follows:

m >>= (\x -> f x >>= g)  &equiv;  (m >>= f) >>= g

Now you might not believe it, but we have already covered some Monads, without even realizing it. Specifically, 
the List Monad generates a list. Let's look a bit more in depth into it.

# List Monad
Now the return function for the List Monad is

```haskell
return x = [x]
```

It justs inserts an element into a list (specifically a single list).

The binding operator is as follows:

```haskell
(>>=) :: [a] -> (a -> [b]) -> b
xs >>= f = concat (map f xs)
```

Basically, the operator maps a function, f, over each element in the list xs. Since f is a function that returns a list, 
the mapping process then returns a list of lists. Then the concat concatenates each element (i.e. singleton list) in the list 
and returns a regular list (i.e. not a list of lists) of our elements. For example let's take xs = [1,2,3] and 
f = \x -> [x\*x] (this notation for a function might confuse you; we will discuss it next in the lambda calculus section). Thus, 
```haskell
[1,2,3] >>= (\x -> [x*x])
= [1, 4, 9]
```

You can run
```haskell
main = do
    print([1,2,3] >>= (\x -> [x*x]))
```
to check if it works for yourself.

Now, you might be thinking that this seems pretty complicated. The thing is, you're not alone. Monads are notoriously 
known for being very confusing, but luckily many [tutorials](https://wiki.haskell.org/Monad_tutorials_timeline) have 
been done covering them in more depth. If you would like to learn even more about them, there are plently of 
[research papers](https://wiki.haskell.org/Research_papers/Monads_and_arrows) written about them. If you want to continue, 
we will now move on to the more theoretical sides of things, starting with [lambda calculus](https://jd-anabi.github.io/functional-programming/lambda-calculus-intro).
