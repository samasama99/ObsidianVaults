- There is three types:
	- Remote (Ex: Promise)
	- Virtual (Ex: cache, virtual threads, lazy evaluation)
	- Protection (Ex: Authorization)

```plantuml
interface ISubject {
	+ request()
}

class RealSubject implements ISubject {
	+ request()
}

class Proxy implements ISubject {
	- realSubject: RealSubject
	+ request()
}
```

