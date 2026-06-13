# Plotting
- **After Update, see Plot window for the result(s).**
## Global configuration
- Grammar: `$T0 {Param}:{Value}`
  - Example of Supported Param:Value pairs
  - zoom:0.5 - 50% zoom level
                        
## 1D Scatter Plot
- Grammar: `$TS {ArrX};{ArrY};{Plot title};{X-axis title};{Y-axis title};{Marker size};{Legend position}`
  - ArrX: 1D array for X values
  - ArrY: 1D or 2D array for Y values. For 2D array, the length of rows should be equal to length of ArrX.
  - Plot title: title of plot, shown on top of plot.
  - X-axis title: title of X-axis, shown on bottom of plot.
  - Y-axis title: title of Y-axis, shown on left of plot.
  - Marker size: size of marker (floating number bet. 0.0~10.0).
  - Legend position: position of legend (see below).
    - UL: UpperLeft
    - UC: UpperCenter
    - UR: UpperRight
    - ML: MiddleLeft
    - MC: MiddleCenter
    - MR: MiddleRight
    - LL: LowerLeft
    - LC: LowerCenter
    - LR: LowerRight
                        
## 2D Heatmap Plot
- Grammar: `$TH {Arr};{Plot title};{X-axis title};{Y-axis title};{Color map}`
  - Arr: 2D array
  - Plot title: title of plot, shown on top of plot.
  - X-axis title: title of X-axis, shown on bottom of plot.
  - Y-axis title: title of Y-axis, shown on left of plot.
  - Color map: color map, shown on right of plot (see below).
    - JT: Jet
    - TB: Turbo
    - VD: Viridis
    - GY: Grayscale
    - TM: Thermal
    - RN: Rain
                        
## Histogram
- Grammar: `$TI {Arr name};{Plot title};{X-axis title};{Y-axis title};{#bins};{bar width};{min. value of X-axis};{max. value of X-axis};{border width};{stats:YN|YS|N};{distribution curve width};{Legend position}`
  - bar width: if 0, width are automatically set
  - stats: 
    - YN - show stats (sample count, mean, sample standard deviation) on legend, with normal distribution curve
    - YS - show stats on legend, with Student's t distribution curve
    - YC - show stats on legend, with Student's t distribution curve scaled with s/Sqrt(n)
    - N - don't show stats, no distribution curve
                        
## Pie chart
- Grammar: `$TP {Value array name};{Labels};{Plot title};{Show percentage:Y/N};{Show values:Y/N};{Show labels:Y/N};{Label color:B|W|F};{Label position:0~1};{Pie size:0~1};{Legend position}`
  - Labels: 
    - label texts separated by comma (','), number of texts should match value array length
  - Label color: 
    - can be one of B, W or F, which corresponds to black, white or same as fill color
                        
## Bar chart
- Grammar: `$TB {Value array name};{Labels};{Series};{Plot title};{X-axis title};{Y-axis title};{Show values:Y/N};{Legend position}`
  - Value array:
    - data in 1D or 2D (for 2D each row -> each series)
  - Series:
    - name of series, total number of names should match name of series
                        
## Box plot
- Grammar: `$TX {Value array names};{Labels};{Plot title};{X-axis title};{Y-axis title};{Show labels:Y/N};{Legend position}`
  - Value array:
    - data in 1D only, names separated by commas
                        
## Stem-and-leaf plot (to Debug window)
- Grammar: `$TF {Value array name};{Plot title}`
  - Value array:
    - data in 1D only

## 3D isometric plot
- Grammar: `$TZ {3D array name};{Plot title};{X-axis title};{Y-axis title};{Z-axis title};{Voxel size};{azimuthal angle, deg.};{transparency: 0.1-1.0};{colormap:JT}`
  - Colormap
    - currently only JT (Jet) colormap is supported

- Example:
```
// Plot of X:1D, Y:1D array pair
$M ArrX[0] {1,2,3,4,5}
$M ArrY[0] {2,4,6,8,10}
$TS ArrX;ArrY;Plot of X:1D Y:1D array pair;X;Y;5;LR
// Plot of X:1D, Y:2D array pair
$M Arr2D[0,0] {1,2,3;2,4,6;3,6,9;4,8,12;5,10,15}
$TS ArrX;Arr2D;Plot of X:1D Y:2D array pair;X;Y;0;UL
// Plot of 2D heatmap
$TH Arr2D;Plot of 2D heatmap;X;Y;JT
// Histogram from uniform distribution
ArrU = ARR.GEN.UNI(2000,1.0,10.0)
$TI ArrU;Histogram;X;Count;20;0.45;1;10;1;N;0;UL
// Histogram plot from normal distribution (no distribution curve)
Arr1 = ARR.GEN.NRM(2000,5.0,1.0)
$TI Arr1;Normal Distribution;X;Count;21;0.45;1;10;1;N;0;UL
// Histogram plot from Student's t distribution (with distribution curve)
Arr1 = ARR.GEN.STU(2000,20,5.0,1.0)
$TI Arr1;Student's t-Distribution;X;Count;21;0.45;1;10;1;YS;1;UL
// Histogram plot from Chi-Squared distribution (without distribution curve)
Arr1 = ARR.GEN.CHI(5000,3)
$TI Arr1;Chi-Squared Distribution;X;Count;50;0.2;1;15;1;N;1;UL
// Histogram plot from Non-central t-distribution (without distribution curve)
Arr1 = ARR.GEN.NCT(1000,10,5)
min = ARR.MIN(Arr1)
max = ARR.MAX(Arr1)
$TI Arr1;Non-central t-distribution;X;Count;20;0.5;1;15;1;N;1;UR
// Mutiple histograms with distribution curves
$M Arr[0,0] {1,1,1,2,2,2,2,3,3,3,3,3,4,4,4,4,5,5,5;6,7,7,8,8,8,8,8,8,9,9,9,10}
ArrT = ARR.TRN(Arr)
$TI ArrT;Histogram;X;Count;20;0.8;1;11;1;YN;1;UL
$TI ArrT;Histogram;X;Count;20;0.95;1;11;0;YS;3;UL
$TI ArrT;Histogram;X;Count;20;0.95;1;11;0;YC;3;UL
// Pie chart
$M arr[0] {100,50,20}
$TP arr;Item1,Item2,Item3;Pie Chart;Y;Y;Y;B;0.6;0.7;UL
// Bar chart
$M arr[0] {100,50,20}
$TB arr;Item1,Item2,Item3;Series1;Bar chart;Items;Values;Y;UL
$M arr2[0,0] {1,2,3,4;2,4,6,8;3,6,9,12}
$TB arr2;Item1,Item2,Item3,Item4;Series1,Series2,Series3;Bar chart;Items;Values;Y;UL
```
- After the update, plots are shown on Plot tab:
```
// Plot of X:1D, Y:1D array pair
$M ArrX[0] {1,2,3,4,5} > OK (5[0~4])
$M ArrY[0] {2,4,6,8,10} > OK (5[0~4])
$TS ArrX;ArrY;Plot of X:1D Y:1D array pair;X;Y;5;LR > OK
// Plot of X:1D, Y:2D array pair
$M Arr2D[0,0] {1,2,3;2,4,6;3,6,9;4,8,12;5,10,15} > OK (5[0~4] × 3[0~2])
$TS ArrX;Arr2D;Plot of X:1D Y:2D array pair;X;Y;0;UL > OK
// Plot of 2D heatmap
$TH Arr2D;Plot of 2D heatmap;X;Y;JT > OK
// Histogram from uniform distribution
ArrU = ARR.GEN.UNI(2000,1.0,10.0) = OK: ArrU (2000[0~1999])
$TI ArrU;Histogram;X;Count;20;0.45;1;10;1;N;0;UL > OK
// Histogram plot from normal distribution (no distribution curve)
Arr1 = ARR.GEN.NRM(2000,5.0,1.0) = OK: Arr1 (2000[0~1999])
$TI Arr1;Normal Distribution;X;Count;21;0.45;1;10;1;N;0;UL > OK
// Histogram plot from Student's t distribution (with distribution curve)
Arr1 = ARR.GEN.STU(2000,20,5.0,1.0) = OK: Arr1 (2000[0~1999])
$TI Arr1;Student's t-Distribution;X;Count;21;0.45;1;10;1;YS;1;UL > OK
// Histogram plot from Chi-Squared distribution (without distribution curve)
Arr1 = ARR.GEN.CHI(5000,3) = OK: Arr1 (5000[0~4999])
$TI Arr1;Chi-Squared Distribution;X;Count;50;0.2;1;15;1;N;1;UL > OK
// Histogram plot from Non-central t-distribution (without distribution curve)
Arr1 = ARR.GEN.NCT(1000,10,5) = OK: Arr1 (1000[0~999])
min = ARR.MIN(Arr1) = 1.77195553067372
max = ARR.MAX(Arr1) = 16.4921630792454
$TI Arr1;Non-central t-distribution;X;Count;20;0.5;1;15;1;N;1;UR > OK
// Mutiple histograms with distribution curves
$M Arr[0,0] {1,1,1,2,2,2,2,3,3,3,3,3,4,4,4,4,5,5,5;6,7,7,8,8,8,8,8,8,9,9,9,10} > OK (2[0~1] × 19[0~18])
ArrT = ARR.TRN(Arr) = OK: ArrT (38[0~18,0~1])
$TI ArrT;Histogram;X;Count;20;0.8;1;11;1;YN;1;UL > OK
$TI ArrT;Histogram;X;Count;20;0.95;1;11;0;YS;3;UL > OK
$TI ArrT;Histogram;X;Count;20;0.95;1;11;0;YC;3;UL > OK
// Pie chart
$M arr[0] {100,50,20} > OK (3[0~2])
$TP arr;Item1,Item2,Item3;Pie Chart;Y;Y;Y;B;0.6;0.7;UL > OK
// Bar chart
$M arr[0] {100,50,20} > OK (3[0~2])
$TB arr;Item1,Item2,Item3;Series1;Bar chart;Items;Values;Y;UL > OK
$M arr2[0,0] {1,2,3,4;2,4,6,8;3,6,9,12} > OK (3[0~2] × 4[0~3])
$TB arr2;Item1,Item2,Item3,Item4;Series1,Series2,Series3;Bar chart;Items;Values;Y;UL > OK
```
