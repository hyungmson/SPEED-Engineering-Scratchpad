# Gauss-Legendre rule/Transformation/Normality Test
- Numerical integration (Gauss-Legendre rule)
  - `ARR.GSL.A({start of interval},{end of interval},{number of points})` - obtain array of abscissas
  - `ARR.GSL.W({start of interval},{end of interval},{number of points})` - obtain array of weights

- Transformation
  - `ARR.TRF.BOC({1D matrix name},{lambda})` - Box-Cox (1964) transformation
    - only works with positive element values
  - `ARR.TRF.YEJ({1D matrix name},{lambda})` - Yeo-Johnson (2000) transformation
    - works with both positive, nagative and zero element values
  - `ARR.TRF.ORQ({1D matrix name})` - Ordered quantile normalization (ORQ) (2019)
    - returns normalized array data
        
- Expanded Shapiro-Wilk test of normality by Royston (1995)
  - `ARR.TST.SWK({1D matrix name},{no. of censored data})`
    - length of matrix should be between 3 and 5000, if not, W,P = 0.0
    - no. of censored data: values that exist conceptually but are not observed because they fall beyond some cutoff (usually right‑censoring in survival analysis).
    - results are contained in 1D array where element values are:
      - W, P

- Example:
```
/ Gauss-Legendre integral
/ 1D integral of x^2 over 0.0~10.0 with 5 points
// obtain array of abscissas
X = ARR.GSL.A(0.0,10.0,5)
// obtain array of weights
W = ARR.GSL.W(0.0,10.0,5)
// summation
sum = 0.0
i = -1
$L1 5
i = i + 1
sum = sum + W[i]*X[i]*X[i]
$L1
$PN "Approximate value is: " sum
/ 2D integral of x^2*y^2 over x:0.0~10.0, y:1.0~2.0 with 5 points in each direction
// obtain array of abscissas
X = ARR.GSL.A(0.0,10.0,5)
Y = ARR.GSL.A(1.0,2.0,5)
// obtain array of weights
WX = ARR.GSL.W(0.0,10.0,5)
WY = ARR.GSL.W(1.0,2.0,5)
// summation
sum = 0.0
i = -1
$L1 5
i = i + 1
j = -1
$L2 5
j = j + 1
sum = sum + WX[i]*WY[j]*X[i]*X[i]*Y[j]*Y[j]
$L2
$L1
$PN "Approximate value is: " sum
/ Expanded Shapiro-Wilk Test
// Data:https://real-statistics.com/tests-normality-and-symmetry
// /statistical-tests-normality-symmetry/shapiro-wilk-expanded-test/
$M arr[0] {65,61,63,86,70,55,74,35,72,68,45,58}
res = ARR.TST.SWK(arr,0)
W = res[0]
p_value = res[1]
/ Normalizing Gamma distribution using ORQ
data = ARR.GEN.GAM(1000,1,1)
data_nrm = ARR.TRF.ORQ(data)
res = ARR.TST.SWK(data,0)
res_nrm = ARR.TST.SWK(data_nrm,0)
p_val = res[1]
p_val_nrm = res_nrm[1]
$TI data,Gamma(1_1),X,Count,20,0.8,0,20,1,N,0,UR
min_nrm = ARR.MIN(data_nrm)
max_nrm = ARR.MAX(data_nrm)
$TI data_nrm,Normalized,X,Count,10,0.8,-4,4,1,N,0,UR
```
- After the update:
```
/ Gauss-Legendre integral
/ 1D integral of x^2 over 0.0~10.0 with 5 points
// obtain array of abscissas
X = ARR.GSL.A(0.0,10.0,5) = OK: X (5[0~4])
// obtain array of weights
W = ARR.GSL.W(0.0,10.0,5) = OK: W (5[0~4])
// summation
sum = 0.0 = 0
i = -1 = -1
$L1 5
i = i + 1 = 4
sum = sum + W[i]*X[i]*X[i] = 333.333333333334
$L1
$PN "Approximate value is: " sum > Approximate value is:  333.333333333334
/ 2D integral of x^2*y^2 over x:0.0~10.0, y:1.0~2.0 with 5 points in each direction
// obtain array of abscissas
X = ARR.GSL.A(0.0,10.0,5) = OK: X (5[0~4])
Y = ARR.GSL.A(1.0,2.0,5) = OK: Y (5[0~4])
// obtain array of weights
WX = ARR.GSL.W(0.0,10.0,5) = OK: WX (5[0~4])
WY = ARR.GSL.W(1.0,2.0,5) = OK: WY (5[0~4])
// summation
sum = 0.0 = 0
i = -1 = -1
$L1 5
i = i + 1 = 4
j = -1 = -1
$L2 5
j = j + 1 = 4
sum = sum + WX[i]*WY[j]*X[i]*X[i]*Y[j]*Y[j] = 777.777777777779
$L2
$L1
$PN "Approximate value is: " sum > Approximate value is:  777.777777777779
/ Expanded Shapiro-Wilk Test
// Data:https://real-statistics.com/tests-normality-and-symmetry
// /statistical-tests-normality-symmetry/shapiro-wilk-expanded-test/
$M arr[0] {65,61,63,86,70,55,74,35,72,68,45,58} > OK (12[0~11])
res = ARR.TST.SWK(arr,0) = OK: res (2[0~1])
W = res[0] = 0.971066436915881
p_value = res[1] = 0.921648863542127
/ Normalizing Gamma distribution using ORQ
data = ARR.GEN.GAM(1000,1,1) = OK: data (1000[0~999])
data_nrm = ARR.TRF.ORQ(data) = OK: data_nrm (1000[0~999])
res = ARR.TST.SWK(data,0) = OK: res (3[0~2])
res_nrm = ARR.TST.SWK(data_nrm,0) = OK: res_nrm (3[0~2])
p_val = res[1] = 0
p_val_nrm = res_nrm[1] = 1
$TI data,Gamma(1_1),X,Count,20,0.8,0,20,1,N,0,UR > OK
min_nrm = ARR.MIN(data_nrm) = -3.29052673149189
max_nrm = ARR.MAX(data_nrm) = 3.29052673149193
$TI data_nrm,Normalized,X,Count,10,0.8,-4,4,1,N,0,UR > OK
```