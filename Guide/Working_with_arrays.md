# Working with arrays
- Array variables has index variables enclosed by square brackets '[]'.
- Grammar: `'variable name' + '[' + 'index1' + ',' + 'index2' + ... + ']'`
- Index can be a integer number or a variable name that contains a integer value.
- **No arithmetic operation is allowed inside the square brackets.**
- **Always create arrays first considering its extent of use.**
- Always update index value in preceding lines.
- The size of index is limited by PC's memory (32 bit), and may slow down the update process (app window may freeze).
- Example:
```
// Create arrays first considering their extent of use
A = ARR.INIT1D(3,0)
F = ARR.INIT3D(3,3,100001,0)
i = 0
A[i] = 1
j = 2
A[j] = 3
C = A[j] + 1
B = A[i] + A[j] + 1
k = i + 1
A[k] = A[i]
// omitted index is defaults to 0: F[2,2] = F[2,2,0]
F[2,2] = A[k]*B
(F[2,2,0])
k = 100000
F[i,j,k] = F[2,2] * B
$P A[0] A[1] A[2] F[2,2] F[i,j,k]
```
- The above example becomes following after 'update'.
```
// Create arrays first considering their extent of use
A = ARR.INIT1D(3,0) = OK: A (3[0~2])
F = ARR.INIT3D(3,3,100001,0) = OK: F (900009[0~2,0~2,0~100000])
i = 0 = 0
A[i] = 1 = 1
j = 2 = 2
A[j] = 3 = 3
C = A[j] + 1 = 4
B = A[i] + A[j] + 1 = 5
k = i + 1 = 1
A[k] = A[i] = 1
// omitted index is defaults to 0: F[2,2] = F[2,2,0]
F[2,2] = A[k]*B = 5
(F[2,2,0]) = 5
k = 100000 = 100000
F[i,j,k] = F[2,2] * B = 25
$P A[0] A[1] A[2] F[2,2] F[i,j,k] > 1 1 3 5 25
```
