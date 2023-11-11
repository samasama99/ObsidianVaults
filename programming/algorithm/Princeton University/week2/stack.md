- how to shrink array:
	- halve size of array s\[\] when array is open-quarter full. 
```java
	public String pop() {
		String item = s[--N];
		s[N] = null; // Loitering
		if (N > 0 && N == s.length / 4) resize(s.length / 2);
		return item;
	}
```
![[Optimization#^61bdad]]

