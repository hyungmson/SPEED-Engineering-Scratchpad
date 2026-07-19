# Plotting
- **After Update, see Plot window for the result(s).**
## Global configuration
- Grammar: `$T0 {Param}:{Value}`
  - Example of Supported Param:Value pairs
  - `zoom:0.5` - 50% zoom level
  - `size:640,480` - plot size set to 640 (width), 480 (height)
  - `fmtX:{format string, e.g., E5, G}` - set x-axis tick format in 2D plot
  - `fmtY:{format string}` - set y-axis tick format in 2D plot
  - `fmtCB:{format string}` - set color bar value format in 2D and 3D plot
  - `axislimit:{x_start},{x_end},{y_start},{y_end}` - set x and y axis limits, set all to 0 (e.g., 0,0,0,0) for automatic fitting
    - Not applicable to pie chart and isometric plot
  - `colorbarlimit:{lower limit},{upper limit}` - set colorbar range, if 0,0 - automatically set
    - Applicable to 2D heatmap, rectangle plot and isometric plot
    
## 1D Scatter Plot
- Grammar (simple): `$TS {ArrX};{ArrY};{Plot title};{X-axis title};{Y-axis title};{Marker size};{Legend position}`
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
- Grammar (new): `$TS {X array names};{Y array names};{Plot title};{X-axis title};{Y-axis title};{Label names};{Line widths};{Marker sizes};{Legend position}`
  - X array names: 1D array names separated by comma
  - Y array names: 1D or 2D array names separated by comma. For 2D array, the length of Y array rows should be equal to length of corresponding X array
  - Number of names in X and Y array should be equal
  - Label names: names separated by comma
  - Line widths: line thicknesses separated by comma
  - Marker sizes: marker sizes separated by comma
                        
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

## 2D Rectangle Plot 
- Heatmap plot with varying cell sizes
- Grammar 1: `$TR {ArrDX};{ArrDY};{Arr2D};{Plot title};{X-axis title};{Y-axis title};{Color map}`
- Grammar 2: `$TR {ArrDX};{ArrDY};{Arr2D};{Plot title};{X-axis title};{Y-axis title};{Cell line thickness};{Cell line color};{Color map}`
  - ArrDX: 1D array of x-direction intervals
  - ArrDY: 1D array of y-direction intervals
  - Arr2D: 2D array having dimension of length(ArrDY) by length(ArrDX)
  - Cell line thickness: input between 0 and 10
  - Cell line color: input from RED,GREEN,BLUE,MAGENTA,SKYBLUE,ORANGE,BROWN,PINK,CYAN,BLACK,WHITE,GREY

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
- Grammar 1: `$TZ {3D array name};{Plot title};{X-axis title};{Y-axis title};{Z-axis title};{Voxel size};{azimuthal angle, deg.};{transparency: 0.1-1.0};{colormap:JT}`
- Grammar 2: $TZ {ArrDX};{ArrDY};{ArrDZ};{3D array name};{Plot title};{X-axis title};{Y-axis title};{Z-axis title};{Voxel size};{azimuthal angle, deg.};{transparency: 0.1-1.0};{colormap:JT}   
  - ArrDX: 1D array of x-direction intervals
  - ArrDY: 1D array of y-direction intervals
  - ArrDZ: 1D array of y-direction intervals
  - Colormap
    - currently only JT (Jet) colormap is supported

- Example:
```
$T0 size:800,480
$T0 fmtCB:F2
// Plot of X:1D, Y:1D array pair
$M ArrX[0] {1,2,3,4,5}
$M ArrY[0] {2,4,6,8,10}
$TS ArrX;ArrY;Plot of X:1D Y:1D array pair;X;Y;5;LR
// Plot of X:1D, Y:2D array pair
$M Arr2D[0,0] {1,2,3;2,4,6;3,6,9;4,8,12;5,10,15}
$TS ArrX;Arr2D;Plot of X:1D Y:2D array pair;X;Y;0;UL
$TS ArrX;Arr2D;Plot of X:1D Y:2D array pair;X;Y;data;2;10;UL
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
// 2D rectangle plot
$M arrDX[0] {1,2,3,4,5}
$M arrDY[0] {2,4,6,8}
$M arr2D[0,0] {1,2,3,4,5;2,3,4,5,6;1,2,3,4,5;2,3,4,5,6}
$TR arrDX;arrDY;arr2D;title;x;y;JT
// 3D isometric plot
$T0 COLORBARLIMIT:0,20
$M arrDX[0] {1,2}
$M arrDY[0] {1,2,3}
$M arrDZ[0] {2,4,2}
$M arr[0,0] {1,2,3;4,5,6;7,8,9;10,11,12;13,14,15;16,17,18}
arr3 = ARR.2DTO3D(arr,1,2)
$PN "2D"
$PM arr
$PN "3D"
$PM arr3
$TZ arrDX;arrDY;arrDZ;arr3;3D isometric plot;x;y;z;30;0.8;22;JT
```
- After the update, plots are shown on Plot tab:
```
$T0 size:800,480 > OK
$T0 fmtCB:F2 > OK
// Plot of X:1D, Y:1D array pair
$M ArrX[0] {1,2,3,4,5} > OK (5[0~4])
$M ArrY[0] {2,4,6,8,10} > OK (5[0~4])
$TS ArrX;ArrY;Plot of X:1D Y:1D array pair;X;Y;5;LR > OK
// Plot of X:1D, Y:2D array pair
$M Arr2D[0,0] {1,2,3;2,4,6;3,6,9;4,8,12;5,10,15} > OK (5[0~4] × 3[0~2])
$TS ArrX;Arr2D;Plot of X:1D Y:2D array pair;X;Y;0;UL > OK
$TS ArrX;Arr2D;Plot of X:1D Y:2D array pair;X;Y;data;2;10;UL > OK
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
// 2D rectangle plot
$M arrDX[0] {1,2,3,4,5} > OK (5[0~4])
$M arrDY[0] {2,4,6,8} > OK (4[0~3])
$M arr2D[0,0] {1,2,3,4,5;2,3,4,5,6;1,2,3,4,5;2,3,4,5,6} > OK (4[0~3] × 5[0~4])
$TR arrDX;arrDY;arr2D;title;x;y;JT > OK
// 3D isometric plot
$T0 COLORBARLIMIT:0,20 > OK
$M arrDX[0] {1,2} > OK (2[0~1])
$M arrDY[0] {1,2,3} > OK (3[0~2])
$M arrDZ[0] {2,4,2} > OK (3[0~2])
$M arr[0,0] {1,2,3;4,5,6;7,8,9;10,11,12;13,14,15;16,17,18} > OK (6[0~5] × 3[0~2])
arr3 = ARR.2DTO3D(arr,1,2) = OK: arr3 (18[0~1,0~2,0~2])
$PN "2D" > 2D
$PM arr > OK
$PN "3D" > 3D
$PM arr3 > OK
$TZ arrDX;arrDY;arrDZ;arr3;3D isometric plot;x;y;z;30;0.8;22;JT > OK
```
