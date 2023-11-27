```java
// this is a Lazy Singleton also not thread safe
class Singleton {
	/*
		Not giving the user the possiblity of creating
		an instance of this class 
	*/
	private Singleton() {}

	private static Singleton instance;
	
	public static Singleton getInstance() {
		if (instance == null) instance = new Singleton();
		return instance;
	}
}
/*  
	one solution is to make the Singleton eager
	the problem is this could be ignored the whole life of the app
	but because it's not lazy it will be wasting memory for no reason 
*/
class Singleton {
	private Singleton() {}

	private static Singleton instance = new Singleton();
	
	public static Singleton getInstance() {
		return instance;
	}
}
/*
	you could make getInstance synchronized
*/
class Singleton {
	private Singleton() {}

	private static Singleton  ;
	
	public static Singleton getInstance() {
		if (instance == null) {
			// class level locking because the method is static
			synchronized (Singleton.class) {
				// the second check because
				// two thread could come at the same time one will
				// be locked until the first exit the scope
				// and second will continue and reinitialize the class
				// if we don't add the second check
				if (instance == null)
					this.instance = new Singleton();
			}
		}
		
		return instance;
	}
}
```

Problems:
- Serialization (you get different instance if you deserialize):
```java
// solution
// adding
class Singleton implements Serializable {
	private Singleton() {}

	private static Singleton instance;
	
	public static Singleton getInstance() {
		if (instance == null) instance = new Singleton();
		return instance;
	}
	// this will ensure during the deserialization that we return the
	// same instance
	protected Object readResolve() {
		return instance;
	}
}
```
- Reflection API (you can make the constructor public):
```java
// solution
public enum EnumSingleton {
	INTANCE;
	public void doSomething() {
		System.out.println("TEST");
	}
}

// how to use 
// ===>  { EnumSingleton.INSTANCE.doSomething(); }
```