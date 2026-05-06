# Fast Fourier Transform
- Fast Fourier Transform
  - `ARR.FFT.PSD({time data},{1D signal data},{output option 0: magnitude (units^2), 1: power (dB)})`
    - returns 2D array where, 1st column contains frequencies linearly varies from 1 to 1/2 of sample range
    - 2nd column contains the magnitude

- Low pass filtering
  - `ARR.FLTR.LPS({time data},{1D signal data},{filtering frequency > 0.0})`
    - returns 2D array where, 1st column contains time data converted to uniform time steps
    - 2nd column contains the filtered signal

- Example:
```
/ Sampling frequency
fs = 1000
T = 1/fs
size = 1000
T_size = T*size
dataX = ARR.INIT.LINE1D(size,0.0,T_size) 
/ Signal
size = size + 1
dataY = ARR.INIT1D(size,0.0)
idx = -1 = -1
pi = UNT.cnt.PI() = 3.14159265358979
$L1 1001
idx = idx + 1 = 199
x = dataX[idx] = 24.875
dataY[idx] = 0.5*Sin(2.0*pi*50*x) + 1.0*Sin(2.0*pi*120*x)
$L1
$TS dataX,dataY,Sin(),t,Sin(),0,UR
/ FFT magnitude
res = ARR.FFT.PSD(dataX,dataY,0)
arrX = ARR.SLICE2D(res,1,0)
arrY = ARR.SLICE2D(res,1,1)
$TS arrX,arrY,Plot,t,Magnitude,0,UR
/ Power spectrum density
res = ARR.FFT.PSD(dataX,dataY,1)
arrX = ARR.SLICE2D(res,1,0)
arrY = ARR.SLICE2D(res,1,1)
$TS arrX,arrY,Plot,t,PSD,0,UR
/ Low pass filter
res = ARR.FLTR.LPS(dataX,dataY,10.0)
arrX = ARR.SLICE2D(res,1,0)
arrY = ARR.SLICE2D(res,1,1)
$TS arrX,arrY,Plot,t,Filtered,0,UR
```
- After the update, peak amplitude/power is observed at 50 and 120 Hz.