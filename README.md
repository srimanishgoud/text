# text

### Assignment Operator

21.  `=` : Assignment operator
    
**Operands**: x (`Variable`), a (`AST`)

**Returns**: (`Float|Int|Bool|Str`) - returns the evaluated value of a

$$Variable=Int  \rightarrow  Int$$

$$Variable=Float  \rightarrow  Float$$

$$Variable=Bool  \rightarrow  Bool$$

$$Variable=Str  \rightarrow  Str$$


manish 

nithish

## Operator Precedence
The Operator Precedence from lowest to highest.
|&nbsp;&nbsp;&nbsp;&nbsp;Name&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;Operators&nbsp;&nbsp;&nbsp;&nbsp;| &nbsp;&nbsp;&nbsp;&nbsp;Associates&nbsp;&nbsp;&nbsp;&nbsp; 
|------------|----------------|----
|assignment    |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;=|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Right
|logicalOr    |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\|\||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Left
|logicalAnd    |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\&\&|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Left
|Equality    |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;==&nbsp;&nbsp;&nbsp;!= |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Left
|Comparison|&nbsp;&nbsp;>&nbsp;&nbsp;&nbsp;>=&nbsp;&nbsp;&nbsp;<&nbsp;&nbsp;&nbsp;<=|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Left
|add|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;+|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Left
|mult|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;*|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Left
|unary|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;~&nbsp;&nbsp;&nbsp;-|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Right
## CFG of the parser
**The Context Free Grammar of our language:**
$$~program  \rightarrow  (declaration)^*~~ EOF$$
$$declaration  \rightarrow  vardec  ~~ | ~~ statement$$
$$statement  \rightarrow  expression ~ Statement ~ | ~ print ~ Statement ~ | ~ if ~ Statement ~ | ~ while ~ Statement ~ | ~ for ~ Statement$$
$$vardec \rightarrow  "var" ~~ identifier ~~ ( ~ "=" ~ expression) ~ ? ~ ";"$$
$$while ~ Statement  \rightarrow  "while" ~~ "(" ~~ expression ~~ ")" ~~ "\{" ~~ declaration ~~ "\}" ~~ $$
$$if ~ Statement  \rightarrow  "if" ~~ "(" ~~ expression ~~ ")" ~~ "\{" ~~ declaration ~~ "\}" ~~ ("else" ~~ "\{" ~~ declaration ~~ "\}")? ~~ $$
$$print ~ Statement  \rightarrow  "zout" ~ "("~ expression ~ ")" ~ ";"$$
$$for ~ Statement  \rightarrow  "for" ~ "("( ~ vardec ~ | ~ expression ~ Statement ~ | ~ ";") ~~ expression? ~~ ";" ~ expression? ~ ")" ~statement$$
$$expression ~ Statement  \rightarrow  expression ~~ ";"$$
$$expression \rightarrow  assignment$$
$$assignment  \rightarrow  identifier "="assignment ~~~ | ~~~ logicOr ~~~ $$
$$logicOr \rightarrow  logicAnd ~~ (~~ "||" ~~ logicAnd ~~ )^* ~~ $$
$$logicAnd \rightarrow  equality ~~ ( ~~ "\And\And" ~~ equality ~~ )^* ~~ $$
$$equality  \rightarrow  comparision ~~ ( ~ ( ~ "!=" ~ | ~ "==" ~ ) ~~ comparision)^* ~~ $$
$$comparision  \rightarrow  add(~ (~ ">"~ |~ ">="~ |~ "<"~ |~ "<="~ )~ add~ )^* ~~ $$
$$add  \rightarrow mult( ~ ("-" ~ | ~ "+") ~ mult)^* ~~ $$
$$mult \rightarrow unary( ~ ("/" ~ | ~ "\*") ~ unary)^* ~~ $$
$$unary  \rightarrow  ("!" ~ | ~ "-") ~ unary ~~ |~~ atom$$
$$atom  \rightarrow  Identifier ~~ | ~~ Int ~~ | ~~ Bool ~~ | ~~ String ~~ | ~~ Float ~~ | ~~ nil ~~ | ~~ "(" ~ expression ~ ")"$$


1. **A print operation that prints values to screen(`PRINT()`)**

   `PRINT()` is used to perform the operation of printing the values to the screen. 
   
   It prints the values to the screen which are given as a list of AST's to it. 
   
   We could also specify the delimiter between the printing values using the keyword `end` , the default delimiter is `" "`.
   
   Suppose we want to put `comma` as the delimiter then we put, `end=", "` 
   
 
2. **Sequential implementation(`Seq()`)**

   We provide the sequence of expressions which we want to execute, as a list. 
   
   Then evaluate each expression and return the value of the last evaluated expression.
   
3. **Truthy(`truthy()`)**

   `truthy(arg)` checks its argument `arg` and classify whether it corresponds to `True` or `False` 
   
   The values that corresponds to False are: 
   
   `Int(0)`, `Float(0)`, `empty dictionary`, `empty string`, `nil`, `False`, `empty list`
   
   Every value other than these correspond to `True`.
