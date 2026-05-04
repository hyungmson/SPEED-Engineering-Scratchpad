# Allowed basic operators
Following basic arithmetic and logical operators can be used along with parentheses.
- Additive: + (addition), - (subtraction)
- Multiplicative: * (multiplication), / (division), % (modulus)
- Exponential: ^ (exponentiation)
- Parentheses: ( ) or { } allowed
- Comparison (return values are '1' for True, '0' for False): 
  - == (equal to)    ex: "val1 = 1 == 2" → 0
  - != (not equal to)    ex: "val1 = 1 != 2" → 1
  - &lt; (less than)    ex: "val1 = 1 &lt; 2" → 1
  - &lt;= (less than or equal to)    ex: "val1 = 1 &lt;= 2" → 1 
  - &gt; (greater than)    ex: "val1 = 1 &gt; 2" → 0
  - &gt;= (greater than or equal to)    ex: "val1 = 1 &gt;= 2" → 0
- Logical (return values are '1' for True, '0' for False): 
  - || (OR)    ex: "val1 = 1 || 0" → 1
  - &amp;&amp; (AND)    ex: "val1 = 1 &amp;&amp; 0" → 0

- **Comparison and logical operators should be used in independent line.**
- **Assign the results to a variable and use that variable in other arithmatic operations.**
- Example:
```
val1 = 1 == 2
val1 = 1 != 2
val1 = 1 < 2
val1 = 1 <= 2
val1 = 1 > 2
val1 = 1 >= 2
val1 = 1 || 0
val1 = 1 && 0
```
