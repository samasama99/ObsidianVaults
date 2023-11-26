**Future Tasks**
Future tasks are tasks with return values, and a future object is a “handle” for accessing a task’s return value. There are two key operations that can be performed on a future object, _A_:

1. _Assignment_ — _A_ can be assigned a reference to a future object returned by a task of the form, _future_ { ⟨ _t__ask-with-return-value_ ⟩ } (using pseudocode notation). The content of the future object is constrained to be _single assignment_ (similar to a final variable in Java), and cannot be modified after the future task has returned.
    
2. _Blocking read_ — the operation, _A.get()_, waits until the task associated with future object _A_ has completed, and then propagates the task’s return value as the value returned by _A.get()_. Any statement, S, executed after A.get() can be assured that the task associated with future object A must have completed before S starts execution.

Some key differences between future tasks and regular tasks in the FJ framework are as follows:

1. A future task extends the [RecursiveTask](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/RecursiveTask.html) class in the FJ framework, instead of [RecursiveAction](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/RecursiveAction.html) as in regular tasks.

2. The compute() method of a future task must have a non-void return type, whereas it has a void return type for regular tasks.

3. A method call like left.join() waits for the task referred to by object left in both cases, but also provides the task’s return value in the case of future tasks.


**Memoization**

The basic idea of “memoization”, which is to remember results of function calls _f_ (_x_) as follows:

1. Create a data structure that stores the set {(x11​, y11​ = f (x11​)), (x22​, y22​ = f(x22​)), . . .} for each call f(xi) that returns yi
    
2. Perform look ups in that data structure when processing calls of the form _f_ (_x'_) when x' equals one of the xi ​inputs for which _f_ (xi​) has already been computed.
    

Memoization can be especially helpful for algorithms based on [dynamic programming](https://en.wikipedia.org/wiki/Dynamic_programming). [Pascal’s triangle](https://en.wikipedia.org/wiki/Pascal%27s_triangle) for example.

The memoization pattern lends itself easily to parallelization using futures by modifying the memoized data structure to store {(x11​, y11​ = future(f(x11​))), (x22​, y22​ = future(f (x22​))), . . .}. The lookup operation can then be replaced by a get() operation on the future value, if a future has already been created for the result of a given input.


**Java Streams**

Java streams provide a #functional approach to operating on collections of data. 
For example, the statement, “students.stream().forEach(s →→ System.out.println(s));”, is a succinct way of specifying an action to be performed on each element s in the collection, _students_. An aggregate data query or data transformation can be specified by building a _stream pipeline_ consisting of a _source_ (typically by invoking the _.stream()_ method on a data collection , a sequence of _intermediate operations_ such as _map()_ and _filter()_, and an optional _terminal operation_ such as _forEach()_ or _average()_. As an example, the following pipeline can be used to compute the average age of all active students using Java streams:

```java
students.stream()

	.filter(s -> s.getStatus() == Student.ACTIVE)
	
	.mapToInt(a -> a.getAge())
	
	.average();
```

An important benefit of using Java streams when possible is that the pipeline can be made to execute in parallel by designating the source to be a _parallel stream_, i.e., by simply replacing _students.stream()_ in the above code by _students.parallelStream()_ or _Stream.of(students).parallel()_. This form of functional parallelism is a major convenience for the programmer, since they do not need to worry about explicitly allocating intermediate collections (e.g., a collection of all active students), or about ensuring that parallel accesses to data collections are properly synchronized.


**Determinism and Data Races**

A parallel program is said to be _functionally deterministic_ if it always computes the same answer when given the same input, and _structurally deterministic_ if it always computes the same computation graph, when given the same input. The presence of data races often leads to functional and/or structural nondeterminism because a parallel program with data races may exhibit different behaviors for the same input, depending on the relative scheduling and timing of memory accesses involved in a data race. In general, the absence of data races is not sufficient to guarantee determinism

**Parallel Loops**
**Barriers in Parallel Loops**
