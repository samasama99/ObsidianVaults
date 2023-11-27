- **S**ingle Responsibility
- **O**pen Closed: close for modifications, open to extension
```java
public class DoThings {
	public void doThingBadPractice(Data data, int flag) {
		switch(flag) {
			case 0:
				// do things
			case 1:
				// do things
			// ....
		}
	}

	public void doThingGoodPractice(Data data, Operation operation) {
		operation.perform(data);
	}
}

public class ImplOp implements Operation {
	@Override
	public void perform(Data data) {
		// perform the operation
	}
}
```

- **L**iskov Substitution
- **I**nterface segregation
- **D**ependency Inversion
```java
public class DoThings {
	// this function depends on those specific operation
	public void doThingBadPractice(Data data, String operation) {
		switch(operation) {
			case "op1":
				OperationOne op = new OperationOne();
				op(data);
			case "op2":
				OperationTwo op = new OperationTwo();
				op(data);
			// ....
		}
	}

	// no dependency
	public void doThingGoodPractice(Data data, Operation operation) {
		operation.perform(data);
	}
}

public class ImplOp implements Operation {
	@Override
	public void perform(Data data) {
		// perform the operation
	}
}
```
