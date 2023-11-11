
 Data Structure:
- Integer array id\[\] of size N.
- Interpretation: id\[i\] is parent of i.
- Root of i is id\[id\[id\[...id\[i\]...\]\]\]
	+ keep going until it doesn't change

exercise : which is the root of 3 and 7, respectively ?

	i       0  1  2  3  4  5  6  7  8  9
	id[i]   0  9  6  5  4  2  6  1  0  5

the root of 3 is 6 :  3 -> 5 -> 2 -> 6
the root of 7 is 6 : 7 -> 1 -> 9 -> 5 -> 2 -> 6

the demo in Excalidraw:
![[Quick-union <lazy approach> demo]]

Quick-union is also slow:
[[Quick-find#^87b7e8]]

algorithm | initialize | union | find
:---: | :---: | :---: | :---: | :---:
#quick-find | N | N | 1
#quick-union | N | N + | N | <- worst case
|||+includes cost of finding roots|

[[Quick-find]] defect.
- Union too expensive (M array accesses).
- Trees are flat, but too expensive to keep them flat
[[Quick-union <lazy approach>]] defect.
- Trees can get tall.
- find too expensive (could be N array accesses).