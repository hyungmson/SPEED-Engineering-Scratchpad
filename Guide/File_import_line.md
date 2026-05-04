# File import line
Lines starting with '$F' becomes file import line.
Use to read CSV (comma separated values) or space seperated values and create matrix variable.
Up to 2-dimensional data can be imported. Blank lines are skipped.
- Grammar: `'$F' 'variable name[start indices]' '{absolute location of CSV file,skip=#,read=@,split=%}'`
- For Android version only
  - {absolute location of CSV file} can be a just {arbitrary file name} which will be replaced with the selected actual file name. So any text would be ok, except blank.
  - **Due to Android policy, file picker will be open each time, and the file has to be manually selected.**
- Put space between command ('$F') and in-between name and values.
- '#' is the number of lines skipped in the import, can be used to skip unnecessary headers.
  - If omitted, 0 skipped lines applied.
- @ is the number of lines read after # skipped lines in the import.
  - If omitted, entire lines are read and used.
- % is the field width of individual number will be parsed from
  - ex: `8|10|5` → first 8 characters, next 10 characters, and next 5 characters will be converted to double and become array elements.
  - If omitted, lines are automatically parsed using comma or space.
- Up to 2 start indices can be defined inside a pair of square brackets separated by comma.
- Becomes starting index number for each direction (row/column) of matrix
  - ex: `mat1[2,5]` → row index starts from 2, column index starts from 5.
- Undefined item in matrix defaults to NaN.
- Example csv file:
  - Below is the contents of CSV file used.
```
# testCSV.csv,,,,,
1,2,3,4,5,6
7,8,9,10,11,12
13,14,15,16,17,18
19,20,21,22,23,24
25,26,27,,, 
```
- Example:
  - Below is the commands in main window:
  - Note that the file location only supports absolute path.
```
$F mat1[0] {D:\testCSV.csv,skip=1}
a = mat1[0]
b = mat1[10]
n = 1
$F mat2[0,0] {D:\testCSV.csv,skip=n}
c = mat2[0,0]
d = mat2[2,3]
```
- From running the above example, mat1 and mat2 become matrices with sizes 1x30 and 5x6, respectively (see below).
- Note that mat1 contains serialized values.
- Unassigned values have a default value of double.MIN.
- Simple variable (ex. 'n') can be used for defining number of skips and reads.
```
$F mat1[0] {D:\testCSV.csv,skip=1} > OK (30[0~29])
a = mat1[0] = 1
b = mat1[10] = 11
n = 1 = 1
$F mat2[0,0] {D:\testCSV.csv,skip=n} > OK (5[0~4] × 6[0~5])
c = mat2[0,0] = 1
d = mat2[2,3] = 16
```
