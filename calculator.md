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
