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
$$logicAnd \rightarrow  equality ~~ (~~ "\&\&" ~~ equality ~~ )^* ~~ $$
$$equality  \rightarrow  comparision ~~ ( ~ ( ~ "!=" ~ | ~ "==" ~ ) ~~ comparision)^* ~~ $$
$$comparision  \rightarrow  add( ~ ( ~ ">" ~ | ~ ">=" ~ | ~ "<" ~ | ~ "<=" ~ ) ~ add ~ )^*$$
$$add  \rightarrow mult( ~ ("-" ~ | ~ "+") ~ mult)^*$$
$$mult  \rightarrow  unary( ~ ("/" ~ | ~ "*") ~ unary ~ )^*$$
$$unary  \rightarrow  ("!" ~ | ~ "-") ~ unary ~~ |~~ atom$$
$$atom  \rightarrow  Identifier ~~ | ~~ Int ~~ | ~~ Bool ~~ | ~~ String ~~ | ~~ Float ~~ | ~~ nil ~~ | ~~ "(" ~ expression ~ ")"$$
