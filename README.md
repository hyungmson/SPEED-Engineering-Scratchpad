# SPEED: Engineering Scratchpad
SPEED, which stands for '**S**cratch **P**aper for **E**fficient **E**ngineering **D**eduction' is a powerful visual notepad.

It is an equation-based line-by-line interpreter where equations and results are displayed simultaneously. Variable names can be utilized and re-used. Array variable is allowed which enables iterative calculation. It is also equipped with CoolProp library and IAPWS-IF97 water property function. Last, it works on plain ASCII text files which can be read and shared easily with others.

Great for on-the-fly, simple to complex engineering calculations. Right companion for solving elementary to practical level engineering problems.

Following features are currently supported.

- Simple to complex arithmetic calculations
- Simultaneous display of equations and results
- Variable assignment based connected calculations
- Array variable supported
- 5 level depth repetition loop
- Text output (echo) manipulation
- 1D, 2D linear interpolation
- Plotting
  - 1D scatter plot
  - 2D heatmap plot
  - 3D isometric plot
  - Histogram
  - Pie chart
  - Bar chart
  - Box plot
  - Stem and leaf plot
- CoolProp fluid property functions
- IAPWS-IF97 light water property calculation
- Linear equation solver (A*x=b)
- Nonlinear solvers
  - Bisection method
  - Golden-section maximization method
  - Particle swarm optimization (PSO) method for minimization
- Extensive statistical functions
  - Check for normality
  - Transformation
  - Tolerance limit factor
- Extensive unit conversion factors
- Other useful functions

Currently available for Android- [Google Play](https://play.google.com/store/apps/details?id=com.blogspot.inherentsafety.SPEED) and Windows- [Microsoft Store](https://apps.microsoft.com/detail/9p9jxs45whvz).
- Latest version: 
  - Windows: 1.0.24
  - Android: Build src 102400 (see Help tab)

## Repository folder structure
- [Guide](https://github.com/hyungmson/SPEED-Engineering-Scratchpad/tree/main/Guide)
  - contains user guide
- Example
  - [Applying_Statistics](https://github.com/hyungmson/SPEED-Engineering-Scratchpad/tree/main/Example/Applying_Statistics)
    - contains SPEED inputs for solving examples in the textbook

## References
- H.-J. Kretzschmar, W. Wagner, International Steam Tables- Properties of Water and Steam Based on the Industrial Formulation IAPWS-IF97</Bold>, 3rd Ed., Springer, 2018.
- P. Blasius, Das Aehnlichkeitsgesetz bei Reibungsvorgangen in Flüssigkeiten, Forschungsheft, Vol. 131, p.1, 1913.
- F. Colebrook, Turbulent Flow in Pipes, with Particular Reference to the Transition Region between Smooth and Round Pipe Laws</Bold>, Journal of the Institution of Civil Engineers, 
  Vol. 11, p.133, 1939.
- S. Haaland, Simple and Explicit Formulas for the Friction Factor in Turbulent Pipe Flow, Journal of Fluid Engineering, Vol. 105, pp. 89-90, 1983.
- F.W. Dittus and L.M.K. Boelter, Heat Transfer in Automobile Radiators of the Tubular Type, University of California Publications in Engineering, Vol. 2, No. 13, pp. 443-461, 1930.
- B.S. Petukhov, Heat Transfer and Friction in Turbulent Pipe Flow with Variable Physical Properties, In: Advances in Heat Transfer, Vol. 6, pp. 503-564, 1970.
- V.V. Gnielinski, Neue Gleichungen für den Wärme- und den Stoffübergang in turbulent durchströmten Rohren und Kanälen, Forschung im Ingenieurwesen A, Vol. 41, pp. 8-16, 1975.
- A. Bar-Cohen W.M. Rohsenow, Thermally Optimum Spacing of Vertical, Natural Convection Cooled, Parallel Plates, Journal of Heat Transfer, Vol. 106, pp. 116-123, 1984.
- D.C. Groeneveld et al, The 2006 CHF look-up table, Nuclear Engineering and Design, Vol. 237, pp. 1909-1922, 2007.
- D.C. Groeneveld, Critical Heat Flux Data Used to Generate the 2006 Groeneveld Lookup Tables, NUREG/KM-0011, USNRC, 2019.
- W.H. Press et al., Numerical Recipes in Fortran 77, 2nd Eds., Cambridge University Press, 1992.
- D. Benton, K. Krishnamoorthy, Computing Discrete Mixtures of Continuous Distributions: Noncentral Chisquare, Noncentral t and the Distribution of the Square of the Sample Multiple Correlation Coefficient, Computational Statistics and Data Analysis, Vol. 43, pp. 249-267, 2003.
- G.E.P. Box and D.R. Cox, An Analysis of Transformations, Journal of the Royal Statistical Society, Series B, Vol. 26, pp. 211-252, 1964.
- I.-K. Yeo and R. Johnson, A New Family of Power Transformations to Improve Normality or Symmetry, Biometrika, Vol. 87, pp. 954-959, 2000.
- J.P. Royston, An Extension of Shapiro and Wilk's W Test for Normality to Large Samples, Applied Statistics, Vol. 31, pp. 115-124, 1982.
- J.P. Royston, Remark AS R94: A Remark on Algorithm AS 181: The W-test for Normality, Applied Statistics, Vol. 44, pp. 547-551, 1995.
- R.B. D'Agostino, An Omnibus Test of Normality for Moderate and Large Size Samples, Biometrika, Vol. 58, pp. 341-348, 1971.
- D. Lurie, L. Abramson, J. Vail, Applying Statistics, NUREG-1475, Rev. 1, USNRC, 2011.
- J. Kiefer, Sequential Minimax Search for a Maximum, Proceedings of the American Mathematical Society, Vol. 4, pp. 502-506, 1953.
- J. Kennedy and R. Eberhart, Particle Swarm Optimization, Proceedings of the IEEE International Conference on Neural Networks,Vol. 4, pp. 1942–1948. 1995.
- J. McCaffrey, Artificial Intelligence: Particle Swarm Optimization, MSDN Magazine, Vol. 26, no. 8, Aug. 2011.
  - https://learn.microsoft.com/en-us/archive/msdn-magazine/2011/august/artificial-intelligence-particle-swarm-optimization (accessed Mar. 14, 2026).
- D.S. Young, tolerance: An R Package for Estimating Tolerance Intervals, Journal of Statistical Software, Vol. 36(5), pp. 1-39, 2010.
- G. Marsaglia, W.W. Tsang, J. Wang, Evaluating Kolmogorov’s Distribution, Journal of Statistical Software, Vol. 8(18), pp. 1–4. 2003.
- R. E. Lund, J. R. Lund, Algorithm AS 190: Probabilities and Upper Quantiles for the Studentized Range, Vol. 32(2), pp. 204-210 Journal of the Royal Statistical Society, 1983.
- M. D. Copenhaver, B. S. Holland, Multiple comparisons of simple effects in the two-way analysis of variance with fixed effects, Journal of Statistical Computation and Simulation, Vol. 30, pp. 1-15, 1988.
- M. Abramowitz, I. A. Stegun, Handbook of Mathematical Functions, Dover publications, Inc. NY, 1970.
- A. H. Stroud, D. Secrest, Gaussian Quadrature Formulas, Prentice-Hall, Inc, NJ, 1966.
  
## Libraries
- Below libraries are used without any modifications.
- CoolProp
  - https://coolprop.org/
- NCalc
  - https://ncalc.github.io/ncalc/
- Math.NET Numerics
  - https://numerics.mathdotnet.com/
- ScottPlot
  - https://github.com/scottplot/scottplot/
- FftSharp
  - https://github.com/swharden/FftSharp
- Fody/Costura
  - https://github.com/Fody/
- WPF.MDI
  - https://github.com/dutts/wpfmdi

## Wkikpedia
- https://en.wikipedia.org/wiki/Greek_letters_used_in_mathematics,_science,_and_engineering
- https://en.wikipedia.org/wiki/Mathematical_operators_and_symbols_in_Unicode
- https://en.wikipedia.org/wiki/List_of_conversion_factors
- https://en.wikipedia.org/wiki/Proton
- https://en.wikipedia.org/wiki/Neutron
- https://en.wikipedia.org/wiki/Compound_interest
- https://en.wikipedia.org/wiki/Weighted_average_cost_of_capital
- https://en.wikipedia.org/wiki/Time_value_of_money
