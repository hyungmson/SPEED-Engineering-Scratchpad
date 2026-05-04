Following functions can be used (case-sensitive).
- For example, "sq1 = Sqrt(0.5)" stores square-root of 0.5 to variable "sq1".
  - Abs(v1), Acos(v1), Asin(v1), Atan(v1), Ceiling(v1), Cos(v1), Exp(v1), Floor(v1), 
  - IEEERemainder(v1,v2), Ln(v1), Log(v1), Log10(v1,v2), Max(v1,v2), Min(v1,v2), Pow(v1,v2),
  - Round(v1,v2), Sign(v1), Sin(v1), Sqrt(v1), Tan(v1), Truncate(v1)

- Example:
```
pi = 3.141592654
val1 = Abs(-2.35)
val1 = Acos(0.5)
val1 = Asin(0.5)
val1 = Atan(0.5)
val1 = Ceiling(3.6)
val1 = Cos(pi/2.0)
val1 = Exp(0.5)
val1 = Floor(3.4)
val1 = IEEERemainder(3.4,3)
val1 = Ln(0.5)
val1 = Log(1.5,2)
val1 = Log(0.5,Exp(1.0))
val1 = Log10(1.5)
val1 = Max(3.0,2.1)
val1 = Min(3.0,2.1)
val1 = Pow(2.0,3.0)
val1 = Round(pi,2)
val1 = Sign(-2.0)
val1 = Sign(3.0)
val1 = Sqrt(4.0)
val1 = Tan(3.5)
val1 = Truncate(3.25)
```
- Following is after the update. Note that due to numerical truncation, Cos(pi/2.0) is not exactly 0, but won't affect the downstream calculation.
```
pi = 3.141592654 = 3.141592654
val1 = Abs(-2.35) = 2.35
val1 = Acos(0.5) = 1.0471975511966
val1 = Asin(0.5) = 0.523598775598299
val1 = Atan(0.5) = 0.463647609000806
val1 = Ceiling(3.6) = 4
val1 = Cos(pi/2.0) = -2.05103428517353E-10
val1 = Exp(0.5) = 1.64872127070013
val1 = Floor(3.4) = 3
val1 = IEEERemainder(3.4,3) = 0.4
val1 = Ln(0.5) = -0.693147180559945
val1 = Log(1.5,2) = 0.584962500721156
val1 = Log(0.5,Exp(1.0)) = -0.693147180559945
val1 = Log10(1.5) = 0.176091259055681
val1 = Max(3.0,2.1) = 3
val1 = Min(3.0,2.1) = 2.1
val1 = Pow(2.0,3.0) = 8
val1 = Round(pi,2) = 3.14
val1 = Sign(-2.0) = -1
val1 = Sign(3.0) = 1
val1 = Sqrt(4.0) = 2
val1 = Tan(3.5) = 0.374585640158595
val1 = Truncate(3.25) = 3
```
