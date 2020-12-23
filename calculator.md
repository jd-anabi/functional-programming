[Back to main](https://jd-anabi.github.io/functional-programming/)

Now that we have a solid grasp on the fundamentals of Haskell, let's apply our knowledge by writing a calculator using the 
parser BNFC. You can install BNFC [here](https://bnfc.digitalgrammars.com/tutorial/bnfc-tutorial.html). Once you have it 
installed, then we are ready to go.

# Grammar
To create our calculator, we first need to define our grammar. First, create a file called *calculator.cf*. Then 
copy this code into it:

```BNFC
Less. Exp ::= Exp "<" Exp1 ;
Greater. Exp ::= Exp ">" Exp1 ;
LEq. Exp ::= Exp "<=" Exp1 ;
GEq. Exp ::= Exp ">=" Exp1 ;
Equal. Exp ::= Exp "==" Exp1 ;

Plus. Exp1 ::= Exp "+" Exp2 ;
Minus. Exp1 ::= Exp "-" Exp2 ;
Times. Exp2 ::= Exp2 "*" Exp3 ;
Divide. Exp2 ::= Exp2 "/" Exp3 ;
Mod. Exp2 ::= Exp2 "%" Exp3 ;
Quot. Exp2 ::= Exp2 "//" Exp3 ;
Rem. Exp2 ::= Exp2 "%%" Exp3 ;
Expon. Exp3 ::= Exp3 "^" Exp4 ;

BTrue. Exp4 ::= "True" ;
BFalse. Exp4 ::= "False" ;
Num. Exp5 ::= Integer ;

coercions Exp 5 ;
```

Now there are two things we want to take away from this. First, we are implementing a calucaltor that has the usual 
addition, subtraction, multiplication, division, exponentitation, and etc. However, this calculator also has the ability 
to evaluate conditionals such as &lte;, &gte;, ==, and more. The second thing we want to take away from this is precedence levels. 
Basically, an expression of higher levels can always be used on expressions of lower levels. The rule coercions Exp 5 ; says that 
5 is the highest level for Exp. You can read more about BNFC [here](https://bnfc.digitalgrammars.com/tutorial/bnfc-tutorial.html). 

# Interpreter.hs and Calculator.hs
Next, copy the following code into files named Interpreter.hs and Calculator.hs respectively.

Interpreter.hs
```haskell
module Interpreter where

import AbsCalculator

eval :: Exp -> Integer
eval (Num n) = n
eval (Plus e1 e2) = (eval e1) + (eval e2)
eval (Times e e') = (eval e) * (eval e')
eval (Minus e1 e2) = (eval e1) - (eval e2)
eval (Divide e1 e2) = (eval e1) `div` (eval e2)
eval (Mod e1 e2) = (eval e1) `mod` (eval e2)
eval (Quot e1 e2) = (eval e1) `quot` (eval e2)
eval (Rem e1 e2) = (eval e1) `rem` (eval e2)
eval (Expon e1 e2) = (eval e1) ^ (eval e2)
eval (BTrue) = 1
eval (BFalse) = 0
eval (Less e1 e2) = if (eval e1) < (eval e2) then 1 else 0
eval (Greater e1 e2) = if (eval e1) > (eval e2) then 1 else 0
eval (LEq e1 e2) = if (eval e1) <= (eval e2) then 1 else 0
eval (GEq e1 e2) = if (eval e1) >= (eval e2) then 1 else 0
eval (Equal e1 e2) = if (eval e1) == (eval e2) then 1 else 0
```

Calculator.hs
```haskell
module Main where

import LexCalculator
import ParCalculator
import AbsCalculator
import Interpreter

import ErrM
import PrintCalculator

main = do
  interact calc
  putStrLn ""

calc s = 
  let Ok e = pExp (myLexer s) 
  in printTree (eval e)

-- ghc Calculator.hs
-- echo "1+2*3" | ./Calculator
```

# Running the Calculator
To run the calculator, first run the command *bnfc -m -haskell calculator.cf*. Then run the command *make*. 
Then run the command *ghc -v Calculator.hs*. Finally, you can test the calculator by running, for example 
*echo "5 + 25" | ./Calculator*. This will compute the expression 5 + 25. However, you can try many other computations, 
like *echo "5 <= 25" | ./Calculator*, which will return 1 (True). You can extend the calculator as you see fit.
