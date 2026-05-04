# Loop line
Lines starting with '$L' becomes loop line.
Used where lengthy repeated update is required. Currently up to **5 depth** level can be processed.
- Grammar: lines to be repeated are situated in between start/end loop lines
- Start loop line contains number of repetition after `$L#` sparated by a space.
  - ex) `$L1 3` ⇽ start level 1 loop with 3 repetition
- '#' is the number between 1~5, which corresponds to level of loop depth.
- End loop line of same depth should always end with same #.
- Higher depth loop commands (start/end) should be enclosed within lower depth loop commands.
```
$L# {number of repetition} ⇽ start loop line
... ⇽ lines to be repeated
$L# ⇽ end loop line
```
- Example:
```
i = 0
j = 0
k = 0
l = 0
m = 0
$L1 2
i = i + 1
$L2 2
j = j + 1
$L3 2
k = k + 1
$L4 2
l = l + 1
$L5 2
m = m + 1
$L5
$L4
$L3
$L2
$P i j k l m
$L1
//
$P i j k l m
```
- As shown in the below, value of i~m differs due to amount of repetition each variable underwent is different.
- If echo command ('$P') is inside the loop, its last echo results are displayed in Main window (see below).
```
i = 0 = 0
j = 0 = 0
k = 0 = 0
l = 0 = 0
m = 0 = 0
$L1 2
i = i + 1 = 2
$L2 2
j = j + 1 = 4
$L3 2
k = k + 1 = 8
$L4 2
l = l + 1 = 16
$L5 2
m = m + 1 = 32
$L5
$L4
$L3
$L2
$P i j k l m > 2 4 8 16 32
$L1
//
$P i j k l m > 2 4 8 16 32
```
- If Debug window is enabled, we can see that the history of echo command ('$P') results with given repetition is displayed (see below).
```
! i j k l m
1 2 4 8 16
! i j k l m
2 4 8 16 32
! i j k l m
2 4 8 16 32
```
