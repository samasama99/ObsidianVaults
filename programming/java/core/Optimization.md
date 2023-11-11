
**Loitering** Holding a reference to an object when it is no longer needed. ^61bdad

```java
	public String pop() {
		return s[--N];
	}
```

VS

```
	public String pop() {
		String item = s[--N];
		s[N] = null;
		return item;
	}
	# this version avoid `loitering`: garbage collector can reclaim memory
	# only if no outstanding reference
```

