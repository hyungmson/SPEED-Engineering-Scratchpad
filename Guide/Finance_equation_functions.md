- `FINA.TAV(P, r, n, t)`: Total accumulated value
  - A = P*(1 + r/n)^(t*n)
  - A: final amount
  - P: original principal sum
  - r: nominal annual interest rate
  - n: compounding frequency (1: annually, 12: monthly, 52: weekly, 365: daily)
  - t: overall length of time the interest is applied (expressed using the same time units as r)
                
- `FINA.MPY(double P, double r, double n)`: Monthly payment
  - c = r*P/(1 - 1/(1+r)^n)
  - c: monthly payment
  - P: principal
  - r: monthly interest rate
  - n: number of payment periods
                
- `FINA.WCC(MVe, MVd, Re, Rd, t)`: Weighted average cost of capital
  - WACC = MVe/(MVd+MVe)*Re + MVd/(MVd+MVe)*Rd*(1-t)
  - WACC: Weighted average cost of capital
  - MVe: amount of financed by one type of shares with the total market value
  - MVd: amount of financed by one type of bonds with the total market value
  - Re: cost of equity (expected return by shareholders)
  - Rd: cost of debt (interest rate on bonds/loans)
  - t: corporate tax rate

- `FINA.PVM(FV, i, n)`: Present value
  - PV = FV/(1+i)^n
  - PV: value at time zero (present value)
  - FV: value at time n (future value)
  - i: interest rate at which the amount componds each period
  - n: number of periods

- Example:
```
P = 1000.0
r = 0.1
n = 1.0
t = 10.0
val = FINA.TAV(P,r,n,t)
val = FINA.MPY(P,r,n)
MVe = 80.0e6
MVd = 20.0e6
Re = 0.1
Rd = 0.05
t = 0.25
val = FINA.WCC(MVe,MVd,Re,Rd,t)
FV = 1000.0
i = 0.1
n = 10.0
val = FINA.PVM(FV,i,n)
```
- After the update:
```
P = 1000.0 = 1000
r = 0.1 = 0.1
n = 1.0 = 1
t = 10.0 = 10
val = FINA.TAV(P,r,n,t) = 2593.7424601
val = FINA.MPY(P,r,n) = 1100
MVe = 80.0e6 = 80000000
MVd = 20.0e6 = 20000000
Re = 0.1 = 0.1
Rd = 0.05 = 0.05
t = 0.25 = 0.25
val = FINA.WCC(MVe,MVd,Re,Rd,t) = 0.0875
FV = 1000.0 = 1000
i = 0.1 = 0.1
n = 10.0 = 10
val = FINA.PVM(FV,i,n) = 385.543289429531
```