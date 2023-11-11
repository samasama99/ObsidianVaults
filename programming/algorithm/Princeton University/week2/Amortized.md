
- amortized cost of adding to a stack using dynamic array : N + (2 + 4 + 8 + ... + N) ~ 3N.
	- N: 1 array access per push.
	- Sum: k array accesses to double to size k (ignoring cost to create new array).
- amortized is the total cost averaged over all the operations.