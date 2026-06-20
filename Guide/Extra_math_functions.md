# Extra math functions
Following functions can be used (case-sensitive).
- Random number calculation
  - `MATH.RANDBET(val1, val2)` - calculate random number between val1 and val2
- Factorial calculation
  - `MATH.FACT(val1)` - calculate factorial of val1
- Bessel functions
  - `MATH.J0(val1)` - calculate value of Bessel function J<sub>0</sub>(val1)
  - `MATH.J1(val1)` - calculate value of Bessel function J<sub>1</sub>(val1)
  - `MATH.Y0(val1)` - calculate value of Bessel function Y<sub>0</sub>(val1)
  - `MATH.Y1(val1)` - calculate value of Bessel function Y<sub>1</sub>(val1)
        
- Other special functions
  - `MATH.GAMA(a)` - Gamma: G(a) = Int_(0,inf) {t^(a-1)*e^(-t)} dx
  - `MATH.GAMA.UINC(a,x)` - Upper incomplete Gamma: G(a,x) = Int_(x,inf) {t^(a-1)*e^(-t)} dx
  - `MATH.GAMA.LINC(a,x)` - Lower incomplete Gamma: g(a,x) = Int_(0,x) {t^(a-1)*e^(-t)} dx
  - `MATH.GAMA.UREG(a,x)` - Upper regularized incomplete Gamma: Q(a,x)= G(a,x)/G(a) 
  - `MATH.GAMA.LREG(a,x)` - Lower regularized incomplete Gamma: P(a,x) = g(a,x)/G(a,x)    
  - `MATH.IGAMA.LREG(a, y)` - Inverse x of lower regularized Gamma: x = P^-1 (a,y)
                        
  - `MATH.BETA(a,b)` - Euler Beta: B(a,b) = Int_(0,1) {t^(a-1)*(1-t)^(b-1)} dt
  - `MATH.BETA.INC(a,b,x)` - Incomplete Beta: B_x (a,b) = Int_(0,x) {t^(a-1)*(1-t)^(b-1)} dt
  - `MATH.BETA.REG(a,b,x)` - Lower incomplete regularized Beta: I_x (a,b) = B(a,b,x)/B(a,b)
                        
  - `MATH.ERRF(x)` - Error: erf(x) = 2/Sqrt(pi)*Int_(0,x) {e^(-t^2)} dt
  - `MATH.IERRF(z)` - Inverse of Error: z = erf^-1 (z)
  - `MATH.ERRF.CMP(x)` - Complementary Error: 1 - erf(x)
  - `MATH.IERRF.CMP(z)` - Invers of complementary Error: x = erfc^-1(z)
                        
  - `MATH.LOGT(x)` - Logistic: 1/{1+e^(-x)}
  - `MATH.ILOGT(y)` - Inverse of Logistic: ln{y/(1-y)}
                        
- Linear interpolation functions **(only works with Arrays)**
  - `MATH.LINE1D(matX,matY,val1)` - calculate interpolated value of matY w.r.t. val1 within matX, matX and matY are 1D arrays and should be of equal length
  - `MATH.LINE2D(matX,matY,matZ,val1,val2)` - calculate interpolated value of matZ w.r.t. val1 within matX, val2 within matY, matX and matY are 1D arrays and matX length should be equal to row size of matZ, matY length should be equal to column size of matZ
                        
- Statistical functions
  - Grammar: `MATH.{Type}.{Distribution}`
  - Type: PDF/PMF - probability, CDF - cumulative, ICDF - inverse cumulative
  - Normal distribution
    - `MATH.PDF.NRM(mean,standard deviation,location)`
    - `MATH.CDF.NRM(mean,standard deviation,location)`
    - `MATH.ICDF.NRM(mean,standard deviation,probability)`
  - Student's t-distribution     
    - `MATH.PDF.STU(mean,standard deviation,degree of freedom,location)`               
    - `MATH.CDF.STU(mean,standard deviation,degree of freedom,location)`
    - `MATH.ICDF.STU(mean,standard deviation,degree of freedom,probability)`
  - Chi-squared distribution
    - `MATH.PDF.CHI(degree of freedom,location)`
    - `MATH.CDF.CHI(degree of freedom,location)`
    - `MATH.ICDF.CHI(degree of freedom,probability)`
  - Non-central t-distribution
    - `MATH.PDF.NCT(degree of freedom,non-central parameter,location)`
    - `MATH.CDF.NCT(degree of freedom,non-central parameter,location)`
    - `MATH.ICDF.NCT(degree of freedom,non-central parameter,probability)`
  - Gamma distribution
    - `MATH.PDF.GAM(shape,rate,location)`
    - `MATH.CDF.GAM(shape,rate,location)`
    - `MATH.ICDF.GAM(shape,rate,probability)`
  - Weibull distribution
    - `MATH.PDF.WBL(shape,scale,location)`
    - `MATH.CDF.WBL(shape,scale,location)`
  - Poisson distribution
    - `MATH.PMF.PSS(lambda,number of occurrences)`
    - `MATH.CDF.PSS(lambda,number of occurrences)`
  - F-distribution
    - `MATH.PDF.FIS(1st degree of freedom,2nd degree of freedom,location)`
    - `MATH.CDF.FIS(1st degree of freedom,2nd degree of freedom,location)`
    - `MATH.ICDF.FIS(1st degree of freedom,2nd degree of freedom,probability)`
  - Lognormal distribution
    - `MATH.PDF.LOGNRM(mean,standard deviation,location)`
    - `MATH.CDF.LOGNRM(mean,standard deviation,location)`
    - `MATH.ICDF.LOGNRM(mean,standard deviation,probability)`
  - Exponential distribution
    - `MATH.PDF.EXP(rate,location)`
    - `MATH.CDF.EXP(rate,location)`
    - `MATH.ICDF.EXP(rate,probability)`
  - Beta distribution
    - `MATH.PDF.BTA(alpha,beta,location)`
    - `MATH.CDF.BTA(alpha,beta,location)`
    - `MATH.ICDF.BTA(alpha,beta,probability)`
  - Hypergeometric distribution
    - `MATH.PMF.HYPGEO(population size,no. of success states in population,number of draws,no. of successes)`
    - `MATH.CDF.HYPGEO(population size,no. of success states in population,number of draws,location)`
  - Binomial distribution
    - `MATH.PMF.BIN(success probability for each trial,number of trials,number of successes)`
    - `MATH.CDF.BIN(success probability for each trial,number of trials,location)`
  - Geometric distribution
    - `MATH.PMF.GEO(success probability for each trial,number of successes)`
    - `MATH.CDF.GEO(success probability for each trial,location)`
  - Negative binomial distribution
    - `MATH.PMF.NEGBIN(no. of successes until experiment is stopped,success probability for each trial,number of successes)`
    - `MATH.CDF.NEGBIN(no. of successes until experiment is stopped,success probability for each trial,location)`
  - Studentized range distribution     
    - `MATH.PDF.STU.RNG(number of groups,number of treatments,dof,location)`                
    - `MATH.CDF.STU.RNG(number of groups,number of treatments,dof,location)`                
    - `MATH.ICDF.STU.RNG(number of groups,number of treatments,dof,probability)`
      - number of groups - (rows) number of independent ranges being considered, usually 1
      - number of treatments  - (columns)number of meanis being compared in a standard one‑way ANOVA with k groups: nTreats = k
      - dof — degrees of freedom of the error term, denominator degrees of freedom from ANOVA: df = N - nTreats
                       
  - Critical F_max value (Hartley’s test)
    - `MATH.FMAX.CRIT(number of groups, degree of freedom, quantile, number of samples)`
    - approximation using Monte Carlo simulation, at least 5000000 samples recommended
                        
  - Tolerance factors
    - `MATH.TOL.K2(number of samples,proportion,confidence)` - calculates k factor for 2-sided tolerance limit for a normal distribution using a method by D.S. Young (2010).      
    - `MATH.TOL.K1(number of samples,proportion,confidence)` - calculates k factor for 1-sided tolerance limit for a normal distribution using an inverse cumulative distribution function for the non-central t-distribution.
      - k_1 = t_(alpha,N-1,delta)/Sqrt(N)
      - delta = z_p*Sqrt(N)
                        
  - Transformation functions for single variable
    - `MATH.TRF.BOC({value},{lambda})` - Box-Cox (1964) transformation
      - only works with positive element values
    - `MATH.TRF.YEJ({value},{lambda})` - Yeo-Johnson (2000) transformation
      - works with both positive, nagative and zero element values
    - `MATH.TRF.ORQ({1D matrix name},{value})` - Ordered quantile normalization (ORQ) (2019)
      - 1D matrix is a raw data before normalization
      - returns normalized value
                        
  - Inverse transformation functions for single variable
    - `MATH.ITRF.BOC({value},{lambda})` - Box-Cox (1964) transformation
      - only works with positive element values
    - `MATH.ITRF.YEJ({value},{lambda})` - Yeo-Johnson (2000) transformation
      - works with both positive, nagative and zero element values
    - `MATH.ITRF.ORQ({1D matrix name},{value})` - Ordered quantile normalization (ORQ) (2019)
      - 1D matrix is a raw data before normalization
      - returns value before normalization
        
  - Normality test by D'Agostino (1971) 
    - normality is accepted if D' of sample is bet. D'_crit(n,alpha/2) and D'_crit(n,1-alpha/2)
    - `MATH.DAGO.D(arr)` - calculates D' test statistic (modified by D. Lurie et al 2011)
      - arr: 1D matrix name
    - `MATH.DAGO.D.CRIT(n,p,size)` - calculates critical D' (modified by D. Lurie et al 2011)
      - n: sample size
      - p: probability level (bet. 0 and 1)
      - size: simulation size (500000 recommended for accurate results)
                        
  - Expanded Shapiro-Wilk test of normality by Royston (1995)
    - `MATH.SWK.W({1D matrix name},{no. of censored data})` - returns W value
      - length of matrix should be between 3 and 5000, if not, W,P = 0.0
      - no. of censored data: values that exist conceptually but are not observed because they fall beyond some cutoff (usually right‑censoring in survival analysis).
    - `MATH.SWK.P({1D matrix name},{no. of censored data})` - returns P value
      - Same as the above.
    - `MATH.SWK.QNT({sample size},{probability})` - returns quantile value
                        
  - P-value calculation functions by Expanded Shapiro-Wilk test of normality by Royston (1995)
    - `MATH.TRF.BOC.P({array name},{lambda})` - p-value from array data after Box-Cox (1964) transformation
    - `MATH.TRF.YEJ.P({array name},{lambda})` - p-value from array data after Yeo-Johnson (2000) transformation

  - Kolmogorov-Smirnov test of normality
    - `MATH.KMV.D({1D matrix name},{mean of normal distribution},{standard deviation of normal distrbution})` - returns D test statistic
    - `MATH.KMV.QNT({sample size},{probability})` - returns quantile value

  - Simple Linear Regression
    - `MATH.FIT.LIN.ICT({X 1D matrix name},{Y 1D matrix name})` - calculates intercept of regression line
    - `MATH.FIT.LIN.SLP({X 1D matrix name},{Y 1D matrix name})` - calculates slope of regression line
    - `MATH.FIT.LIN.R2({X 1D matrix name},{Y 1D matrix name})` - calculates coefficient of determination (R^2) of regression line
    - 
  - Correlation
    - `MATH.Sxx({X 1D matrix name})` - calculates squared sum of X_i - X_avg
    - `MATH.Sxy({X 1D matrix name},{Y 1D matrix name})` - calculates sum of (X_i - X_avg)*(Y_i - Y_avg)
    - `MATH.Rxy({X 1D matrix name},{Y 1D matrix name})` - calculates correlation coefficient

  - Auxilliary functions         
    - `MATH.SDVP({1D array name})` - calculates population standard deviation of 1D array
    - `MATH.SDVS({1D array name})` - calculates sample standard deviation of 1D array
    - `MATH.COVP({1D array name})` - calculates coefficient of variation of population of 1D array
    - `MATH.COVS({1D array name}) `- calculates coefficient of variation of sample of 1D array
    - `MATH.KURT({1D array name})` - calculates Kurtosis of 1D array
    - `MATH.SKEW({1D array name})` - calculates skewness of 1D array
    
    - `MATH.MED({1D array name})` - calculate median
    - `MATH.MEN.GEO({1D array name})` - calculate geometric mean
    - `MATH.MEN.HAR({1D array name})` - calculate harmonic mean
    - `MATH.QRT.LWR({1D array name})` - calculate lower quartile
    - `MATH.QRT.UPR({1D array name})` - calculate upper quartile
    - `MATH.IQR({1D array name})` - calculate Inter Quartile Range (IQR)
    - `MATH.PCT({1D array name},{percentile in integer})` - calculate percentile
    - `MATH.QNT({1D array name},{quantile in float})` - calculate quantile
                         
    - `MATH.NPR(n,r)` - calculates permutation of getting r elements from n elements
    - `MATH.NCR(n,r)` - calculates combination of getting r elements from n elements
   
    - `MATH.SUM.SQA({array name})` - sum of squares
    - `MATH.SUM.CUB({array name})` - sum of cubes
    - `MATH.AVG.SQA({array name})` - average of squares
    - `MATH.AVG.CUB({array name})` - average of cubes
    - `MATH.AVG.SQA.ADJ({array name})` - adjusted sum of squares (sum of squares - correction)
   
    - `MATH.CtoF({temperature in Celcius})` - converts Celcius to Fahrenheit
    - `MATH.FtoC({temperature in Fahrenheit})` - converts Fahrenheit to Celcius

- Example:
```
(MATH.RANDBET(1.0,10.0))
(MATH.FACT(5))
x = 0.6
(MATH.J0(x))
(MATH.J1(x))
(MATH.Y0(x))
(MATH.Y1(x))
//
$M matX[0] {1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0}
$M matY[0] {10.0,20.0,30.0,40.0,50.0,60.0,70.0,80.0,90.0,100.0}
y = MATH.LINE1D(matX,matY,8.4)
//
$M matX[0] {1.0,2.0,3.0}
$M matY[0] {1.0,2.0,3.0,4.0,5.0}
$M matZ[0,0] {10.0,20.0,30.0,40.0,50.0;60.0,70.0,80.0,90.0,100.0;110.0,120.0,130.0,140.0,150.0}
//     1.0  2.0  3.0  4.0  5.0
// 1.0 10.0,20.0,30.0,40.0,50.0;
// 2.0 60.0,70.0,80.0,90.0,100.0;
// 3.0 110.0,120.0,130.0,140.0,150.0
z = MATH.LINE2D(matX,matY,matZ,2.2,4.4)
/ Statistical functions
n = 10000
mean = 0.0
sd = 1.0
pr = 0.95
/ critical values
// from normal distribution
z = MATH.ICDF.NRM(mean,sd,pr)
// from Student's-t distribution
c = MATH.ICDF.STU(mean,sd,n,pr)
// from Chi-Squared distribution
n = 42
q = MATH.ICDF.CHI(n,pr)
/ k factor for 2-sided tolerance limit for a normal distribution
// https://www.itl.nist.gov/div898/handbook/prc/section2/prc263.htm
n = 43
p = 0.9
a = 0.99
(MATH.TOL.K2(n,p,a))
/ k factor for 1-sided tolerance limit for a normal distribution
// https://www.itl.nist.gov/div898/handbook/prc/section2/prc263.htm
(MATH.TOL.K1(n,p,a))
/ standard deviations
$M arr[0] = {1,2,3,4,5,6,7,8,9,10}
// sd of population
sdp = MATH.SDVP(arr)
// sd of sample
sds = MATH.SDVS(arr)
```
- After the update:
```
(MATH.RANDBET(1.0,10.0)) = 2.19429920389983
(MATH.FACT(5)) = 120
x = 0.6 = 0.6
(MATH.J0(x)) = 0.912004862832889
(MATH.J1(x)) = 0.286700988056671
(MATH.Y0(x)) = -0.308509867975477
(MATH.Y1(x)) = -1.26039134650313
//
$M matX[0] {1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0,10.0} > OK (10[0~9])
$M matY[0] {10.0,20.0,30.0,40.0,50.0,60.0,70.0,80.0,90.0,100.0} > OK (10[0~9])
y = MATH.LINE1D(matX,matY,8.4) = 84
//
$M matX[0] {1.0,2.0,3.0} > OK (3[0~2])
$M matY[0] {1.0,2.0,3.0,4.0,5.0} > OK (5[0~4])
$M matZ[0,0] {10.0,20.0,30.0,40.0,50.0;60.0,70.0,80.0,90.0,100.0;110.0,120.0,130.0,140.0,150.0}
> OK (3[0~2] × 5[0~4])
//     1.0  2.0  3.0  4.0  5.0
// 1.0 10.0,20.0,30.0,40.0,50.0;
// 2.0 60.0,70.0,80.0,90.0,100.0;
// 3.0 110.0,120.0,130.0,140.0,150.0
z = MATH.LINE2D(matX,matY,matZ,2.2,4.4) = 104
/ Statistical functions
n = 10000 = 10000
mean = 0.0 = 0
sd = 1.0 = 1
pr = 0.95 = 0.95
/ critical values
// from normal distribution
z = MATH.ICDF.NRM(mean,sd,pr) = 1.95996398454005
// from Student's-t distribution
c = MATH.ICDF.STU(mean,sd,n,pr) = 1.96020123990555
// from Chi-Squared distribution
n = 42 = 42
q = MATH.ICDF.CHI(n,pr) = 58.124037680868
/ k factor for 2-sided tolerance limit for a normal distribution
// https://www.itl.nist.gov/div898/handbook/prc/section2/prc263.htm
n = 43 = 43
p = 0.9 = 0.9
a = 0.99 = 0.99
(MATH.TOL.K2(n,p,a)) = 2.21731589665363
/ k factor for 1-sided tolerance limit for a normal distribution
// https://www.itl.nist.gov/div898/handbook/prc/section2/prc263.htm
(MATH.TOL.K1(n,p,a)) = 1.87395360584732
/ standard deviations
$M arr[0] {1,2,3,4,5,6,7,8,9,10} > OK (10[0~9])
// sd of population
sdp = MATH.SDVP(arr) = 2.87228132326901
// sd of sample
sds = MATH.SDVS(arr) = 3.02765035409749
```
