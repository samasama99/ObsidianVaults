- **autoboxing** automatically cast between a primitive type and its wrapper.
```java
Stack<Integer> s = new Stack<Integer>();
s.push(17); // s.push(new Integer(17));
int s = s.pop(); // int a = s.pop().intValue();
```
