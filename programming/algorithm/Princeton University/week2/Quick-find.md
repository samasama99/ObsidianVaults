-  [Algorithms-Princeton-University/Week1 at main · samasama99/Algorithms-Princeton-University (github.com)](https://github.com/samasama99/Algorithms-Princeton-University/tree/main/Week1)

The demo in Excalidraw: ![[Quick-find demo]]

Java implementation:
```java
public class QuickFindUF {

	private int[] id;

	public QuickFindUF(int N) {
		id = new int[N];

		for (int i = 0;i < N;i++) {
			id[i] = i;
		}
	}

	public boolean connected(int p, int q) {
		return id[p] == id[q];
	}

	public void union(int p, int q) {
		int pid = id[p];
		int qid = id[q];
	
		for (int i = 0;i < id.length; i++) {
			// NOTE id[p] will change that's why we use pid instead of id[p]
			if (id[i] == pid) {
				id[i] = qid;
			}
		}
	}
}
```

Quick-find is too slow:

algorithm | initialize | union | find
:---: | :---: | :---: | :---:
#quick-find | N | N | 1

^87b7e8




