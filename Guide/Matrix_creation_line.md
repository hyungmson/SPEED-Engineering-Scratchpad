# Matrix creation line
Lines starting with '$M' becomes matrix creation line.
Use to create and assign values to the matrix variable, up to 2-dimensional data can be inserted.
For 3D array creation, use ARR.INIT3D function.
- Grammar: `'$M' 'variable name[start indices]' '{values separated by comma/semicolon}'`
- Put space between command ('$M') and in-between name and values
- Values after semicolon (';') becomes data for next row
- up to 2 start indices can be defined inside a pair of square brackets separated by comma.
- Becomes starting index number for each direction (row/column) of matrix.
  - ex: `mat1[2,5]` → Row index starts from 2, column index starts from 5.
- Undefined item in matrix defaults to NaN.
- Example:
```
$M mat0[0] {1,2,3,4,5,6,7,8,9,10}
a = mat0[5]
b = mat0[0] + mat0[8]
$M mat1[0] {1,2,3,4,5,6,7;8,9,10,11,12}
c = mat1[0]
d = mat1[1] + mat1[7]
$M mat2[0,0] {1,2,3,4,5,6,7;8,9,10,11,12}
e = mat2[1,1]
f = mat2[0,0] + mat2[0,1]
$M mat10[10,10] {1,2,3,4,5,6,7;8,9,10,11,12;13,14,15,16,17}
g = mat10[10,10]
```
- From running the above example, mat0, mat1, mat2, and mat10 become matrices with sizes 1x10, 1x14 (=2x7), 2x7, and 3x7, respectively.
- Size and available index ranges are displayed inside paranthesis.
- Note that mat1 contains serialized values.
- Unassigned values have a default value of double.MIN.
- As shown in the below after update, starting indices of mat10 becomes 10,10.
```
$M mat0[0] {1,2,3,4,5,6,7,8,9,10} > OK (10[0~9])
a = mat0[5] = 6
b = mat0[0] + mat0[8] = 10
$M mat1[0] {1,2,3,4,5,6,7;8,9,10,11,12} > OK (14[0~13])
c = mat1[0] = 1
d = mat1[1] + mat1[7] = 10
$M mat2[0,0] {1,2,3,4,5,6,7;8,9,10,11,12} > OK (2[0~1] × 7[0~6])
e = mat2[1,1] = 9
f = mat2[0,0] + mat2[0,1] = 3
$M mat10[10,10] {1,2,3,4,5,6,7;8,9,10,11,12;13,14,15,16,17} > OK (3[10~12] × 7[10~16])
g = mat10[10,10] = 1
```
