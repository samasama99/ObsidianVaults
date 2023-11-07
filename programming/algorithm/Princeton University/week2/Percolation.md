
- TODO: 
	- [ ] the row and column indices are integers between 1 and _n_, where (1, 1) is the upper-left site: Throw an `IllegalArgumentException` if any argument to `open()`, `isOpen()`, or `isFull()` is outside its prescribed range. Throw an `IllegalArgumentException` in the constructor if _n_ ≤ 0.
	- [ ] _Performance requirements._  The constructor must take time proportional to _n_2; all instance methods must take constant time plus a constant number of calls to `union()` and `find()`.
	- **Monte Carlo simulation.** To estimate the percolation threshold, consider the following computational experiment:
		- [ ] Initialize all sites to be blocked.
		- Repeat the following until the system percolates:
		   -  [ ] Choose a site uniformly at random among all blocked sites.
		   -  [ ] Open the site.
		- The fraction of sites that are opened when the system percolates provides an estimate of the percolation threshold.