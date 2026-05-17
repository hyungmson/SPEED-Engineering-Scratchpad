# Array functions
- **This feature only works with arrays.**
- **Due to performance issues, only single array function is allowed per line.**

- Following functions are applicable to 1D and 2D arrays.
- Average value calculation
  - `ARR.AVG({matrix name})`             
- Sum value calculation
  - `ARR.SUM({matrix name})`     
- Number of elements (ignores blank element) calculation
  - `ARR.CNT({matrix name})`       
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
                        
- Matrix slicing to lower dimension
    - `ARR.SLICE2D({2D matrix name},{i-th dimension to be fixed: 0 or 1},{index j to be fixed at})`
      - creates 1D array where its elements coresponds to j-th index of i-th dimension
      - ex. `ARR.SLICE2D(mat0,0,2)`: 1D array from 2-th row
    - `ARR.SLICE3D({3D matrix name},{i-th dimension to be fixed: 0~2},{index j to be fixed at})`
      - creates 2D array where its elements coresponds to j-th index of i-th dimension
      - ex. `ARR.SLICE3D(mat0,1,5)`: 2D array (of 1st and 3rd dimensions) from 5-th column
                        
- Additional functions
  - `ARR.TRN({2D matrix name, A})` - transpose of A = A'
  - `ARR.DIA({row size (=col. size)},{initialization value})` - diagonal matrix creation  
  - `ARR.REM.MAX({1D array name})` - returns array with maximum value(s) removed
  - `ARR.REM.MIN({1D array name})` - returns array with minimum value(s) removed
                        
- Linear algebra
  - `ARR.SOLVE({2D matrix name, A},{1D matrix name, b})` - solves A*x = b for x
  - `ARR.DOT({2D matrix name, A},{1D matrix name, b})` - scalar product between A and b
                        
- Element-wise binary operation
  - `ARR.OPEL.B({matrix name, A},{matrix name, B},{operator})`
    - matrix A and B can be 1D, 2D or 3D matrix.
    - dimensions and shapes (# of rows, columns, or depths) of A and B should be same.
    - allowed operator strings: + (add), - (subtract), * (multiply), / (division), ^ (power)
  - `ARR.OPEL.U({matrix name, A},{double value, B},{operator})`
    - same as OPEL.B, but element-wise operation is done with element of A and value B
                        
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
```
