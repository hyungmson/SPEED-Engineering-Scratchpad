# Array functions
- **This feature only works with arrays.**
- **Due to performance issues, only single array function is allowed per line.**

- Following functions are applicable to 1D and 2D arrays.
- Average value calculation
  - `ARR.AVG({matrix name})`
  -  `ARR.AVG2D({2D matrix name},{calculation direction: 0 - row, 1 - column})` - create 1D array where each element is row- or column-wise average
- Sum value calculation
  - `ARR.SUM({matrix name})`
  - `ARR.SUM2D({2D matrix name},{calculation direction: 0 - row, 1 - column})` - create 1D array where each element is row- or column-wise sum
- Variance calculation
  - `ARR.VARS2D({2D matrix name},{calculation direction: 0 - row, 1 - column})` - create 1D array where each element is row- or column-wise sample variance
- Number of elements (ignores blank element) calculation
  - `ARR.CNT({matrix name})`
  - `ARR.CNT2D({2D matrix name},{calculation direction: 0 - row, 1 - column})` - create 1D array where each element is row- or column-wise count
- Maximum value calculation
  - `ARR.MAX({matrix name})` - calculate maximum value
  - `ARR.MAX0({matrix name})` - find 1st (row) index of maximum value element
  - `ARR.MAX1({matrix name})` - find 2nd (column) index of maximum value element  
  - `ARR.MAX2({matrix name})` - find 3rd (depth) index of maximum value element
- Minimum value calculation
  - `ARR.MIN({matrix name})` - calculate minimum value
  - `ARR.MIN0({matrix name})` - find 1st (row) index of minimum value element
  - `ARR.MIN1({matrix name})` - find 2nd (column) index of minimum value element   
  - `ARR.MIN2({matrix name})` - find 3rd (depth) index of minimum value element  
- Matrix creation with specified initializtion
  - `ARR.INIT1D({size of 1st dimension},{initialization value})` - creates 1D array
  - `ARR.INIT2D({size of 1st dimension},{size of 2nd dimension},{initialization value})` - creates 2D array
  - `ARR.INIT3D({size of 1st dimension},{size of 2nd dimension},{size of 3rd dimension},{initialization value})` 
    - creates 3D array
  - `ARR.INIT.LINE1D({number of equal length sections},{minumum value},{maximum value})` 
    - creates 1D array containing n+1 points equally spaced between max. and min. values
        
- Array sort
  - `ARR.SORT.ASC({1D matrix name})` - returns 1D array of elements sorted in ascending order
  - `ARR.SORT.DEC({1D matrix name})` - returns 1D array of elements sorted in descending order

- Binning
  - `ARR.BIN.CNT({1d matrix name},{1d bin boundary array name},{remove duplicate in boundary array (0:no|1:yes)})` - returns 1D array of counts per bin
    - number of bins = size(1d matrix) + 1

- Matrix slicing to lower dimension
    - `ARR.SLICE2D({2D matrix name},{i-th dimension to be fixed: 0 or 1},{index j to be fixed at})`
      - creates 1D array where its elements coresponds to j-th index of i-th dimension
      - ex. `ARR.SLICE2D(mat0,0,2)`: 1D array from 2-th row
    - `ARR.SLICE3D({3D matrix name},{i-th dimension to be fixed: 0~2},{index j to be fixed at})`
      - creates 2D array where its elements coresponds to j-th index of i-th dimension
      - ex. `ARR.SLICE3D(mat0,1,5)`: 2D array (of 1st and 3rd dimensions) from 5-th column
                        
- Additional functions
  - `ARR.TRN({2D matrix name, A})` - transpose of A = A'
  - `ARR.FLIP1D({1D array name})` - returns flipped array
  - `ARR.FLIP2D({2D array name},{flip direction row axis:0|colum axis:1})` - returns flipped array
  - `ARR.DIA({row size (=col. size)},{initialization value})` - diagonal matrix creation  
  - `ARR.REM.MAX({1D array name})` - returns array with maximum value(s) removed
  - `ARR.REM.MIN({1D array name})` - returns array with minimum value(s) removed
  - `ARR.REM.VAL({1D array name},{element value to be removed})` - returns array with specified value element(s) removed
  - `ARR.RANK1D({1D array name})` - returns array with ranks, replace ties with their mean
  - `ARR.RANK2D({2D array name},{ranking direction:0|1|2})` - returns array with ranks, replace ties with their mean, rank for blank elements are given 0 value
    - ranking direction: 0: ranking for entire array, 1: ranking for each row, 2: ranking for each column
  - `ARR.APND1D({1D array #1},{1D array #2})` - returns array #2 appended to array #1
  - `ARR.SET.UNI({1D array #1},{1D array #2})` - returns set union
  - `ARR.SET.DIS({1D array})` - returns set distinct (removes duplicate values)
  - `ARR.SET.EXC({1D array #1},{1D array #2})` - returns set difference
  - `ARR.SET.INT({1D array #1},{1D array #2})` - returns set intersection
                                   
- Linear algebra
  - `ARR.SOLVE({2D matrix name, A},{1D matrix name, b})` - solves A*x = b for x
  - `ARR.DOT({2D matrix name, A},{1D matrix name, b})` - scalar product between A and b
                        
- Element-wise binary operation
  - `ARR.OPEL.B({matrix name, A},{matrix name, B},{operator})`
    - matrix A and B can be 1D, 2D or 3D matrix.
    - dimensions and shapes (# of rows, columns, or depths) of A and B should be same.
    - allowed operator strings: + (add), - (subtract), * (multiply), / (division), ^ (power), log (logarithm with B as base value), rem (remainder of A/B),
      - = (comparison) : +1 for A > B, -1 for A < B, 0 for A=B
      - `>` (comparison) : 1 for A > B, 0 for A < B or A=B
      - < (comparison) : 1 for A < B, 0 for A > B or A=B
  - `ARR.OPEL.U({matrix name, A},{double value, B},{operator})`
    - same as OPEL.B, but element-wise operation is done with element of A and value B
    - additional allowed operator strings (only A value is used, enter 0 for B): 
      - exp (exponential), ln (natural log), sin (sine), cos (cosine), tan (tangent), ! (factorial), abs (absolute), round (round to B digits)

- Cumulative distribution
  - `ARR.CDF({1D matrix name})`
    - returns cumulative sum of given matrix (F(y))
- Complementary cumulative distribution
  - `ARR.CDFC({1D matrix name})`
    - returns complementary cumulative sum of given matrix (1-F(y))
      
- 1D array creation with random values with distribution
  - `ARR.GEN.UNI({size},{min},{max})`
    - initialize numbers from uniform distribution
    - see histogram plot example in the below
  - `ARR.GEN.NRM({size},{mean},{standard deviation})` 
    - initialize numbers from normal distribution
    - see histogram plot example in the below
  - `ARR.GEN.STU({size},{degree of freedom},{mean},{standard deviation})` 
    - initialize numbers from Student's t-distubtion
    - see histogram plot example in the below
  - `ARR.GEN.CHI({size},{degree of freedom})` 
    - initialize numbers from Chi-Squared distubtion
    - see histogram plot example in the below
  - `ARR.GEN.NCT({size},{degree of freedom},{non-centrality parameter})`
    - initialize numbers from non-central t-distubtion
    - see histogram plot example in the below
  - `ARR.GEN.GAM({size},{shape},{rate})`
    - initialize numbers from Gamma distribtion
  - `ARR.GEN.WBL({size},{shape},{scale})`
    - initialize numbers from Weibull distribution
  - `ARR.GEN.PSS({size},{lambda})`
    - initialize numbers from Poisson distribution
  - `ARR.GEN.FIS({size},{1st degree of freedom},{2nd degree of freedom})`
    - initialize numbers from F-distribution
  - ARR.GEN.LOGNRM({size},{mean},{standard deviation}) 
    - initialize numbers from lognormal distribution
  - ARR.GEN.EXP({size},{rate})
    - initialize numbers from exponential distribution
  - ARR.GEN.BTA({size},{alpha},{beta})
    - initialize numbers from beta distribution
                        
- Column-wise 1D/2D matrix concatenation
  - `ARR.CAT.COL({matrix name, A},{matrix name, B})`
    - returns A|B 2D matrix
    - blank elements are filled with double.min value
    - the element with double.min value are shown as blank in Debug window, and blank in heatmap

- Obtain line numbers of search string from file
  - `ARR.FNDL.STR@{search string}@{full file path with extension}`
    - returns 1D array containing line numbers where search string is contained
    - if file doesn't exist or the contents doesn't contain search string, "Not OK" is printed\
    - ex. `arr = ARR.FNDL.STR@output temperature@D:\output.dat`

- Obtain 2D data from texts containing series of multiline data (chunk) separated by spaces
  - `ARR.READ.STR.2D(file path, 1D array name containing start lines, lines read per chunk, start column, field widths of individual numbers)`
    - ex: field widths = 0 -> line will be parsed by spaces
    - ex: field widths = 8|10|5 -> first 8 characters, next 10 characters, and next 5 characters will be converted to double and become array elements

- Obtain reduced 2D data
  - `ARR.CHOP2D(2D matrix name, start row, end row, start column, end column)`
    - selects data bound by 4 bound argument (start row, end row, start column, end column) and returns as 2D array 
    - all 4 bound arguments are zero based indices
    - if start row or start column is -1, it defaults to 0 (start index)
    - if end row or end column is -1, it defaults to row and column size of input 2D matrix, respectively

- Convert array to higher dimension
  - `ARR.1DTO2D({1D array name},{collection size})` 
    - converts 1D array to 2D array by stacking constant number of elements
  - `ARR.2DTO3D({2D matrix name},{1:collect by rows|0:by columns},{collection size})`
    - collects 2D data by constant number of rows or columns and stacks to return 3D array

- Convert array to lower dimension
  - `ARR.2DTO1D({2D array name},{0:concatenate rows|1:by columns})`
    - convert 2D array to 1D array by concatenating rows or columns
 
- Generate interpolated data
  - `ARR.INTP1D({X grid array name},{X array name},{Y array name})` - returns 1D linearly interpolated data
  - `ARR.INTP2D({X grid array name},{Y grid array name},{X array name},{Y array name},{Z array name})` - returns 2D linearly interpolated data
    - X, Y, Z arrays need to be of same lengths    

- Replaces part of array data
  - `ARR.REPL1D({target 1D array name},{insertion 1D array name},{start index, 0-based})` 
    - replaces portion of target 1D array with value from insertion array with offset
  - `ARR.REPL2D({target 2D array name},{insertion 2D array name},{1st dimension start index, 0-based},{2nd dimension start index, 0-based})` 
    - replaces portion of target 2D array with value from insertion array with offset
  - `ARR.REPL3D({target 3D array name},{insertion 3D array name},{1st dimension start index, 0-based},{2nd dimension start index, 0-based},{3rd dimension start index, 0-based})` 
    - replaces portion of target 3D array with value from insertion array with offset
   
- Example:
```
$M mat0[0] {1,2,3,4,5,6,7,8,9,10} 
// find average value and check with manual calculation
val = ARR.AVG(mat0)
(1+2+3+4+5+6+7+8+9+10)/10
iMin = ARR.MIN0(mat0)
$M mat10[10,10] {1,2,3,4,5,6,7;8,9,10,11,12;13,14,15,16,17} 
val = ARR.AVG(mat10)
(1+2+3+4+5+6+7+8+9+10+11+12+13+14+15+16+17)/17
// find indices of max/min value elements
iMin = ARR.MIN0(mat10)
jMin = ARR.MIN1(mat10)
iMax = ARR.MAX0(mat10)
jMax = ARR.MAX1(mat10)
// find max/min values
val = mat10[iMax,jMax]
val = ARR.MAX(mat10)
val = mat10[iMin,jMin]
val = ARR.MIN(mat10)
// calculate sum/number of elements
val = ARR.SUM(mat10)
val = ARR.CNT(mat10)
// 3D array creation filled with 0s
(ARR.INIT3D(2,3,2,0))
$PM mat0
// modify element value
mat0[0,0,0] = 1.0
mat0[0,1,0] = 2.0
mat0[0,2,0] = 3.0
mat0[1,0,0] = 4.0
mat0[1,1,0] = 5.0
mat0[1,2,0] = 6.0
mat0[0,0,1] = 7.0
mat0[0,1,1] = 8.0
mat0[0,2,1] = 9.0
mat0[1,0,1] = 10.0
mat0[1,1,1] = 11.0
mat0[1,2,1] = 12.0
// check a designated element value is modified
(mat0[0,1,0])
(mat0[1,2,1])
$PN "After mod"
$PM mat0
// 2D matrix from slice at 1st dimension index fixed at 0 (1st row)
mat1 = ARR.SLICE3D(mat0,0,0)
$PN "mat1"
$PM mat1
// 2D matrix from slice at 2nd dimension index fixed at 2 (3rd column)
mat2 = ARR.SLICE3D(mat0,1,2)
$PN "mat2"
$PM mat2
// 2D matrix from slice at 3rd dimension index fixed at 1 (2nd page)
mat3 = ARR.SLICE3D(mat0,2,1)
$PN "mat3"
$PM mat3
// 1D matrix from slice at 1st dimension index fixed at 1 (1st row)
mat4 = ARR.SLICE2D(mat3,0,1)
$PN "mat4"
$PM mat4
// Transpose
mat5 = ARR.TRN(mat3)
$PN "mat5"
$PM mat5
// Create diagonal matrix
mat6 = ARR.DIA(5,1.5)
$PN "mat6"
$PM mat6
// linear algebra solver, 
// Ref.: https://numerics.mathdotnet.com/LinearEquations
$M matA[0,0] {3,2,-1;2,-2,4;-1,0.5,-1}
$M matB[0] {1,-2,0}
(ARR.SOLVE(matA,matB))
(vec_x[0])
(vec_x[1])
(vec_x[2])
matX = ARR.SOLVE(matA,matB)
(matX[0])
(matX[1])
(matX[2])
// 2D matrix - 1D vector scalar product
V1 = ARR.DOT(matA,matB)
$PM V1
// Element-wise binary operation
$M A[0,0] {1,2,3;4,5,6;7,8,9}
$M B[0,0] {1,2,3;4,5,6;7,8,9}
C = ARR.OPEL.B(A,B,+)
$PN "A+B"
$PM C
C = ARR.OPEL.B(A,B,-)
$PN "A-B"
$PM C
C = ARR.OPEL.B(A,B,*)
$PN "A*B"
$PM C
C = ARR.OPEL.B(A,B,/)
$PN "A/B"
$PM C
C = ARR.OPEL.B(A,B,^)
$PN "A^B"
$PM C
// Colum-wise matrix concatenation
$M Arr1D_1[0] {1,2,3,4,5}
$M Arr1D_2[0] {6,7,8,9,10}
$M Arr2D_1[0,0] {11,12,13,14,15;16,17,18,19,20;21,22,23,24,25}
$M Arr2D_2[0,0] {-1,-2,-3,-4,-5;-6,-7,-8,-9,-10;-11,-12,-13,-14,-15}
resArr = ARR.CAT.COL(Arr1D_1,Arr1D_2)
$PN "1D|1D"
$PM resArr
resArr = ARR.CAT.COL(Arr1D_1,Arr2D_1)
$PN "1D|2D"
$PM resArr
resArr = ARR.CAT.COL(Arr2D_1,Arr1D_2)
$PN "2D|1D"
$PM resArr
$TH resArr,Plot of 2D heatmap,X,Y,JT
resArr = ARR.CAT.COL(Arr2D_1,Arr2D_2)
$PN "2D|2D"
$PM resArr
$T0 zoom:0.35
$TH resArr,Plot of 2D heatmap,X,Y,JT
// 2D interpolation and flip
X = ARR.INIT.LINE1D(9,1,10)
Y = ARR.INIT.LINE1D(9,2,20)
Z = ARR.OPEL.B(X,Y,*)
res2D = ARR.INTP2D(X,Y,X,Y,Z)
$TH res;Plot of 2D heatmap;X;Y;JT
res2D1 = ARR.FLIP2D(res2D,0)
$TH res2D1;Plot of 2D heatmap, flip0;X;Y;JT
res2D2 = ARR.FLIP2D(res2D,1)
$TH res2D2;Plot of 2D heatmap, flip1;X;Y;JT
// Array append and set functions
$M arr1[0] {1,2,3,4,5,3}
$M arr2[0] {3,4,5,6,7,8,8,9}
arr = ARR.APND1D(arr1,arr2)
$PM arr
arr = ARR.SET.UNI(arr1,arr2)
$PM arr
arr = ARR.SET.DIS(arr1)
$PM arr
arr = ARR.SET.EXC(arr1,arr2)
$PM arr
arr = ARR.SET.INT(arr1,arr2)
$PM arr
// replace 1D array data
$M arr1Dtgr[0] {0,1,2,3,4,5,6,7,8,9}
$M arr1Dins[0] {10,20,30}
res1D = ARR.REPL1D(arr1Dtgr,arr1Dins,2)
$PM res1D
// replace 2D array data
$M arr2Dtgr[0,0] {0,1,2,3,4;5,6,7,8,9;10,11,12,13,14}
$M arr2Dins[0,0] {-1,-2;-3,-4}
res2D = ARR.REPL2D(arr2Dtgr,arr2Dins,1,2)
$PM res2D
```
- After the update:
```
$M mat0[0] {1,2,3,4,5,6,7,8,9,10} > OK (10[0~9])
// find average value and check with manual calculation
val = ARR.AVG(mat0) = 5.5
(1+2+3+4+5+6+7+8+9+10)/10 = 5.5
iMin = ARR.MIN0(mat0) = 0
$M mat10[10,10] {1,2,3,4,5,6,7;8,9,10,11,12;13,14,15,16,17} > OK (3[10~12] × 7[10~16])
val = ARR.AVG(mat10) = 9
(1+2+3+4+5+6+7+8+9+10+11+12+13+14+15+16+17)/17 = 9
// find indices of max/min value elements
iMin = ARR.MIN0(mat10) = 10
jMin = ARR.MIN1(mat10) = 10
iMax = ARR.MAX0(mat10) = 12
jMax = ARR.MAX1(mat10) = 14
// find max/min values
val = mat10[iMax,jMax] = 17
val = ARR.MAX(mat10) = 17
val = mat10[iMin,jMin] = 1
val = ARR.MIN(mat10) = 1
// calculate sum/number of elements
val = ARR.SUM(mat10) = 153
val = ARR.CNT(mat10) = 17
// 3D array creation filled with 0s
(ARR.INIT3D(2,3,2,0)) = OK: mat0 (12[0~1,0~2,0~1])
$PM mat0 > OK
// modify element value
mat0[0,0,0] = 1.0 = 1
mat0[0,1,0] = 2.0 = 2
mat0[0,2,0] = 3.0 = 3
mat0[1,0,0] = 4.0 = 4
mat0[1,1,0] = 5.0 = 5
mat0[1,2,0] = 6.0 = 6
mat0[0,0,1] = 7.0 = 7
mat0[0,1,1] = 8.0 = 8
mat0[0,2,1] = 9.0 = 9
mat0[1,0,1] = 10.0 = 10
mat0[1,1,1] = 11.0 = 11
mat0[1,2,1] = 12.0 = 12
// check a designated element value is modified
(mat0[0,1,0]) = 2
(mat0[1,2,1]) = 12
$PN "After mod" > After mod
$PM mat0 > OK
// 2D matrix from slice at 1st dimension index fixed at 0 (1st row)
mat1 = ARR.SLICE3D(mat0,0,0) = OK: mat1 (6[0~2,0~1])
$PN "mat1" > mat1
$PM mat1 > OK
// 2D matrix from slice at 2nd dimension index fixed at 2 (3rd column)
mat2 = ARR.SLICE3D(mat0,1,2) = OK: mat2 (4[0~1,0~1])
$PN "mat2" > mat2
$PM mat2 > OK
// 2D matrix from slice at 3rd dimension index fixed at 1 (2nd page)
mat3 = ARR.SLICE3D(mat0,2,1) = OK: mat3 (6[0~1,0~2])
$PN "mat3" > mat3
$PM mat3 > OK
// 1D matrix from slice at 1st dimension index fixed at 1 (1st row)
mat4 = ARR.SLICE2D(mat3,0,1) = OK: mat4 (3[0~2])
$PN "mat4" > mat4
$PM mat4 > OK
// Transpose
mat5 = ARR.TRN(mat3) = OK: mat5 (6[0~2,0~1])
$PN "mat5" > mat5
$PM mat5 > OK
// Create diagonal matrix
mat6 = ARR.DIA(5,1.5) = OK: mat6 (25[0~4,0~4])
$PN "mat6" > mat6
$PM mat6 > OK
// linear algebra solver,
// Ref.: https://numerics.mathdotnet.com/LinearEquations
$M matA[0,0] {3,2,-1;2,-2,4;-1,0.5,-1} > OK (3[0~2] × 3[0~2])
$M matB[0] {1,-2,0} > OK (3[0~2])
(ARR.SOLVE(matA,matB)) = OK: vec_x (3[0~2])
(vec_x[0]) = 1
(vec_x[1]) = -2
(vec_x[2]) = -2
matX = ARR.SOLVE(matA,matB) = OK: vec_x (3[0~2])
(matX[0]) = 1
(matX[1]) = -2
(matX[2]) = -2
// 2D matrix - 1D vector scalar product
V1 = ARR.DOT(matA,matB) = OK: V1 (3[0~2])
$PM V1 > OK
$M A[0,0] {1,2,3;4,5,6;7,8,9} > OK (3[0~2] × 3[0~2])
$M B[0,0] {1,2,3;4,5,6;7,8,9} > OK (3[0~2] × 3[0~2])
C = ARR.OPEL.B(A,B,+) = OK: C (9[0~2,0~2])
$PN "A+B" > A+B
$PM C > OK
C = ARR.OPEL.B(A,B,-) = OK: C (9[0~2,0~2])
$PN "A-B" > A-B
$PM C > OK
C = ARR.OPEL.B(A,B,*) = OK: C (9[0~2,0~2])
$PN "A*B" > A*B
$PM C > OK
C = ARR.OPEL.B(A,B,/) = OK: C (9[0~2,0~2])
$PN "A/B" > A/B
$PM C > OK
C = ARR.OPEL.B(A,B,^) = OK: C (9[0~2,0~2])
$PN "A^B" > A^B
$PM C > OK
// Colum-wise matrix concatenation
$M Arr1D_1[0] {1,2,3,4,5} > OK (5[0~4])
$M Arr1D_2[0] {6,7,8,9,10} > OK (5[0~4])
$M Arr2D_1[0,0] {11,12,13,14,15;16,17,18,19,20;21,22,23,24,25} > OK (3[0~2] × 5[0~4])
$M Arr2D_2[0,0] {-1,-2,-3,-4,-5;-6,-7,-8,-9,-10;-11,-12,-13,-14,-15} > OK (3[0~2] × 5[0~4])
resArr = ARR.CAT.COL(Arr1D_1,Arr1D_2) = OK: resArr (10[0~4,0~1])
$PN "1D|1D" > 1D|1D
$PM resArr > OK
resArr = ARR.CAT.COL(Arr1D_1,Arr2D_1) = OK: resArr (30[0~4,0~5])
$PN "1D|2D" > 1D|2D
$PM resArr > OK
resArr = ARR.CAT.COL(Arr2D_1,Arr1D_2) = OK: resArr (30[0~4,0~5])
$PN "2D|1D" > 2D|1D
$PM resArr > OK
$TH resArr,Plot of 2D heatmap,X,Y,JT > OK
resArr = ARR.CAT.COL(Arr2D_1,Arr2D_2) = OK: resArr (30[0~2,0~9])
$PN "2D|2D" > 2D|2D
$PM resArr > OK
$T0 zoom:0.35 > OK
$TH resArr,Plot of 2D heatmap,X,Y,JT > OK
// 2D interpolation and flip
X = ARR.INIT.LINE1D(9,1,10) = OK: X (10[0~9])
Y = ARR.INIT.LINE1D(9,2,20) = OK: Y (10[0~9])
Z = ARR.OPEL.B(X,Y,*) = OK: Z (10[0~9])
res2D = ARR.INTP2D(X,Y,X,Y,Z) = OK: res (100[0~9,0~9])
$TH res;Plot of 2D heatmap;X;Y;JT > OK
res2D1 = ARR.FLIP2D(res2D,0) = OK: res1 (100[0~9,0~9])
$TH res2D1;Plot of 2D heatmap, flip0;X;Y;JT > OK
res2D2 = ARR.FLIP2D(res2D,1) = OK: res2 (100[0~9,0~9])
$TH res2D2;Plot of 2D heatmap, flip1;X;Y;JT > OK
// Array append and set functions
$M arr1[0] {1,2,3,4,5,3} > OK (6[0~5])
$M arr2[0] {3,4,5,6,7,8,8,9} > OK (8[0~7])
arr = ARR.APND1D(arr1,arr2) = OK: arr (14[0~13])
$PM arr > OK
arr = ARR.SET.UNI(arr1,arr2) = OK: arr (9[0~8])
$PM arr > OK
arr = ARR.SET.DIS(arr1) = OK: arr (5[0~4])
$PM arr > OK
arr = ARR.SET.EXC(arr1,arr2) = OK: arr (2[0~1])
$PM arr > OK
arr = ARR.SET.INT(arr1,arr2) = OK: arr (3[0~2])
$PM arr > OK
// replace 1D array data
$M arr1Dtgr[0] {0,1,2,3,4,5,6,7,8,9} > OK (10[0~9])
$M arr1Dins[0] {10,20,30} > OK (3[0~2])
res1D = ARR.REPL1D(arr1Dtgr,arr1Dins,2) = OK: res1D (10[0~9])
$PM res1D > OK
// replace 2D array data
$M arr2Dtgr[0,0] {0,1,2,3,4;5,6,7,8,9;10,11,12,13,14} > OK (3[0~2] × 5[0~4])
$M arr2Dins[0,0] {-1,-2;-3,-4} > OK (2[0~1] × 2[0~1])
res2D = ARR.REPL2D(arr2Dtgr,arr2Dins,1,2) = OK: res2D (15[0~2,0~4])
$PM res2D > OK
```
- The above example generates following in Debug window.
```
0,0,0
0,0,0
0,0,0
0,0,0
After mod
1,2,3
4,5,6
7,8,9
10,11,12
mat1
1,7
2,8
3,9
mat2
3,9
6,12
mat3
7,8,9
10,11,12
mat4
10,11,12
mat5
7,10
8,11
9,12
mat6
1.5,0,0,0,0
0,1.5,0,0,0
0,0,1.5,0,0
0,0,0,1.5,0
0,0,0,0,1.5
-1,6,-2
A+B
2,4,6
8,10,12
14,16,18
A-B
0,0,0
0,0,0
0,0,0
A*B
1,4,9
16,25,36
49,64,81
A/B
1,1,1
1,1,1
1,1,1
A^B
1,4,27
256,3125,46656
823543,16777216,387420489
1D|1D
1,6
2,7
3,8
4,9
5,10
1D|2D
1,11,12,13,14,15
2,16,17,18,19,20
3,21,22,23,24,25
4,,,,,
5,,,,,
2D|1D
11,12,13,14,15,6
16,17,18,19,20,7
21,22,23,24,25,8
,,,,,9
,,,,,10
2D|2D
11,12,13,14,15,-1,-2,-3,-4,-5
16,17,18,19,20,-6,-7,-8,-9,-10
21,22,23,24,25,-11,-12,-13,-14,-15
1,2,3,4,5,3,3,4,5,6,7,8,8,9
1,2,3,4,5,6,7,8,9
1,2,3,4,5
1,2
3,4,5
0,1,10,20,30,5,6,7,8,9
0,1,2,3,4
5,6,-1,-2,9
10,11,-3,-4,14
```
