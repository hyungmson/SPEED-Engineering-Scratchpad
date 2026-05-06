# Equation solver
- **For below methods, only functions with single numeric return value can be used within the expression.**
- **It is suggested to wrap each variable name in parenthesis to deal with negative numbers correctly.**
- **Due to performance issue, array variable names cannot be used within the expression.**
## Global configuration
- Grammar: `$S0 {Param}:{Value}`
  - Example of Supported Param:Value pairs
    - `AERR:0.00001` - absolute error between expression value and target = 1e-5 (default value: 1e-6)
    - `NMAX:1000` - maximum iteration = 1000 (default value: 1000)
  - Below 3 are for Particle Swarm Optimization solver
    - [reference link](https://learn.microsoft.com/en-us/archive/msdn-magazine/2011/august/artificial-intelligence-particle-swarm-optimization)
    - `PSO.W:0.729` - inertia weight (default value = 0.729)
    - `PSO.C1:1.49445` - cognitive/local weight (default value = 1.49445)
    - `PSO.C2:1.49445` - social/global weight (default value = 1.49445)
    - `PSO.NP:10` - number of particles (default value = 10)
                        
## Bisection method
- Grammar: `$SB {expression}={target value};{indep. var name}:{lower bound}~{upper bound}`
  - expression: single line expression.
  - target value: **set to 0**.
  - indep. var name: independent variable name.
  - lower bound: lower bound of indep. variable used in bisection method.
  - upper bound: upper bound of indep. variable used in bisection method. 
                        
## Golden-section maximization method
- Grammar: `$SB {expression}={target value};{indep. var name}:{lower bound}~{upper bound}`
  - expression: single line expression.
  - target value: **set to 0**.
  - indep. var name: independent variable name.
  - lower bound: lower bound of indep. variable used in golden-section method.
  - upper bound: upper bound of indep. variable used in golden-section method. 
                        
## Particle swarm optimization (PSO) method for minimization
- Grammar: `$SP {expression}={target value};{indep. var name #1}|{indep. var name #2}|...:{lower bound #1}~{upper bound #1}|{lower bound #2}~{upper bound #2}|...`
  - expression: single line expression.
  - target value: **set to 0**.
  - indep. var name: independent variable name.
  - lower bound: lower bound of indep. variable used in PSO method.
  - upper bound: upper bound of indep. variable used in PSO method.

- Example:
  - variables in below examples are wrapped in parenthesis to deal with negative value
```
// configuration line for solver
$S0 AERR:1.0e-6
$S0 NMAX:1000
y = 27.0
// Solve for x using Bisection method
$SB x^3 - y = 0;x:0.0~10.0
// Solve for x using Golden-section method to maximize the function value
$SG -(x+5)^2 + 5 = 0;x:-10.0~10.0
// Solve using Particle Swarm Optimization (Minimization) method
$SP x*Exp(-((x)^2+(y)^2)) + 0.4288819 = 0;x|y:-100.0~100.0|-100.0~100.0
y = 27.0 = 27
$SP Abs((x)^3 - (y)) = 0;x:-10.0~10.0
```
- After the update (n: number of iterations, f: final expression value):
```
// configuration line for solver
$S0 AERR:1.0e-6 > OK
$S0 NMAX:1000 > OK
y = 27.0 = 27
// Solve for x using Bisection method
$SB x^3 - y = 0;x:0.0~10.0 > Good x:2.99999997019768 (n:26,f:-8.04662636966214E-07)
// Solve for x using Golden-section method to maximize the function value
$SG -(x+5)^2 + 5 = 0;x:-10.0~10.0 > Good x:-5.0000000353551 (n:35,f:5)
// Solve using Particle Swarm Optimization (Minimization) method
$SP x*Exp(-((x)^2+(y)^2)) + 0.4288819 = 0;x|y:-100.0~100.0|-100.0~100.0 > Good x:-0.707446487987507;y:0.000793087761494778; (n:131,f:3.26251883897566E-07)
y = 27.0 = 27
$SP Abs((x)^3 - (y)) = 0;x:-10.0~10.0 > Good x:2.99999998159258; (n:134,f:4.97000339549913E-07)
```