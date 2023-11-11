
###### random notes:

Week 1:

- ReciprocalArraySum using RecursiveAction's in Java's Fork/Join Framework (Demo)
	- change increase the number of processors used 

```java
System.setProperty("java.util.concurent.ForkJoinPoll.common.parallelism", "2");
```

Week 2:

- Data race happens in **read-write** or **write-write** situation.
- benign non determinism is when the result is acceptable even if the result is different every time, like a search algorithm running in parallel 

 | functional det                        | structural det                        | determinism                            |
 | --------------------------- | --------------------------- | ---------------------------- |
 | same input -> same output | same input -> comp graph | drf -> funcl det + struct det  |

* DRF = data race freedom

