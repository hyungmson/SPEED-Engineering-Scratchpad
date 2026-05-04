# Echo line
Line starting with '$P' becomes an echo line.
Used for printing out variable values in desired order.    
- **Grammar 1**: `$P 'variable name1' 'variable name2' ...`
- Put a space between command ('$P') and in-between each variable names
- If '$PN' is used, comment line is omitted in Debug window.
- Example:
```
w_ch = 66.6e-3
t_ch = 2.35e-3
A_ch = w_ch*t_ch
$P w_ch t_ch A_ch
```
- The above example gets right-appended with corresponding values after 'update':
```
w_ch = 66.6e-3 = 0.0666
t_ch = 2.35e-3 = 0.00235
A_ch = w_ch*t_ch = 0.00015651
$P w_ch t_ch A_ch > 0.0666 0.00235 0.00015651
```

- **Grammar 2**: `$P {'fmt1' 'fmt2' ...} 'var name1' 'var name2' ...`
- fmt1, fmt2 corresponds to C#-style format string and entire format strings should be put inside single pair of curly brackets, separated by spaces ({ }).
- Format string grammar: 'W:F#' for numeric data, 'W' for string data
  - W is total character width, F is format specifier such as 'F', 'E', ...
  - '#' is number of decimal places      
- Other format string examples: 
  - `W:0.00E+0` → -9.00E+1
  - `W:0.00e+0` → -9.00e+1
  - `W:000` → 001 (fill the preceding placeholder with 0s)
- Put space between command ('$P') and each format strings and variable names
- Example:
```
Val1 = 12.325987
Val2 = 102.57891
number = 001
$P {10:E2} Val1
$P {4:F0 8:F4} Val1 Val2
$P {8:F2} Val1 Val2
$P {5 3:000 8:F2} "Card" number Val1
```
- The above example gets right-appended with formatted values after 'update'.
- If the number of format strings is less than number of variable names, last format string is applied to the rest of variable names and corresponding format strings are inserted (see line 5 of example).
```
Val1 = 12.325987 = 12.325987
Val2 = 102.57891 = 102.57891
number = 001 = 1
$P {10:E2} Val1 > 1.23E+001
$P {4:F0 8:F4} Val1 Val2 >  12102.5789
$P {8:F2 8:F2} Val1 Val2 >   12.33  102.58
$P {5 3:000 8:F2} "Card" number Val1 > Card001   12.33
```

- **Grammar 3**: `$PM 'matrix name'`
- Prints out matrix contents to Debug window.
- Note that only numeric values are printed (including header contents will trigger error).
- Content of 3D array is displayed as a sequence of 2D slices along 1st and 2nd dimensions, iterated over each index of 3rd dimensions.
- Example:
```
$M mat10[10,10] {1,2,3,4,5,6,7;8,9,10,11,12;13,14,15,16,17}
$PN "mat10"
$PM mat10
```
- The above example generates following in Debug window.
- Note that unassigned value position is printed with blank.
```
mat10
1,2,3,4,5,6,7
8,9,10,11,12,,
13,14,15,16,17,,
```  
