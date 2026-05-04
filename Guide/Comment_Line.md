# Comment line
Line starting with '#', '*', '+', '/' or '!' becomes comment line.
In "Style" mode (for Windows version only), comment lines can be colored other than black using below command. 
Default value is red, brown, magenta, orange and blue, respectively. On wrong command, black color is used.

- Grammar: `$0 COLOR.{start character}:{color}`
  - available {start character} values: #, /, *, +, !
  - available {color} values: RED, GREEN, BLUE, MAGENTA, SKYBLUE, ORANGE, BROWN, PINK, CYAN, BLACK

Also, the color of line starting with $ can be changed using below command. 
Default value is green.  On wrong command, black color is used.
- Grammar: `$0 COLOR.$:{color}`
  - Comment line contents are ignored in calculation and will remain as-is after update. 
  - Texts following these comment characters won't have any effect on calculation.

- Example:
```
$0 COLOR.$:GREEN
$0 COLOR.#:RED
$0 COLOR.*:BROWN
$0 COLOR./:MAGENTA
$0 COLOR.+:ORANGE
$0 COLOR.!:BLUE
# Comment 1
## Comment 2
### Comment 3
* Comment 4
** Comment 5
*** Comment 6
+ Comment 7
++ Comment 8
+++ Comment 9
/ Comment 10
// Comment 11
/// Comment 12
```
