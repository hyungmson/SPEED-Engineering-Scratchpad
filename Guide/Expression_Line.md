# Expression line
This is the line where actual calculation is made.
2 types of calculations can be made, one with and without assignment to a variable.

## Pure calculation line
The line starting with parenthesis ('(', '{') and numbers (0~9) are pure calculation line, 
where the calculated value cannot be re-used.
- Floating point numeric values should be written with '.' even if it doesn't have decimal values.
- Without '.', SPEED may understand it as an integer type,
    which is subject to floating point error during arithmatic operation.
- ex) Use 3000.0 istead of 3000.
- **Wrap the variable name which may contain negative numbers in parenthesis**
- Example:
```
# Friction factor using Zigrang-Sylvester (1982) explicit formula
1.0/{-2.0*Log10((0.002/5.0)/3.7-5.02/45000.0*Log10((0.002/5.0)/3.7-5.02/45000.0*Log10((0.002/5.0)/3.7+13.0/45000.0)))}^2.0
```

## Assignment line
The line must start with alphabetical characters.        
- Grammar: 'variable name' + ' = ' + 'expression'
- On expression side, only variable names where their values are already assigned or calculated can be used.
- Assignment operator ('=') must be **surrounded by spaces** to become **' = '**.
  - (except the assignment operator, other operators don't require surrounding spaces. But recommended to do so.)
- Variable names are **case-sensitive**.
- Example:
```
# Conversion factor
mm_to_m = 0.001
// Geometric variables
t_ch = 2.35 * mm_to_m
w_ch = 66.6 * mm_to_m
Ac_ch = t_ch * w_ch
```
- In lines 4 and 5, 't_ch', and 'w_ch' get values '2.35e-3' and '66.6e-3', respectively.
- In line 6, 'Ac_ch' gets calculation result of '1.5651e-4'.
- The above example gets right-appended with numeric data after 'update':
```
# Conversion factor
mm_to_m = 0.001 = 0.001
// Geometric variables
t_ch = 2.35 * mm_to_m = 0.00235
w_ch = 66.6 * mm_to_m = 0.0666
Ac_ch = t_ch * w_ch = 0.00015651
```
