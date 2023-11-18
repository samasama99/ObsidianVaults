- Abstraction in java #UML #class_diagram
![[class_diagram]]

- note: class diagram is closer to code
- Encapsulation in java and Uml:

| Student                       |
| ----------------------------- |
| - gpa: float                  |
| - degreeProgram: String       |
| -----------------------------   |
| + getGpa(): float             |
| + getDegreeProgram() : String |

- Association:

```plantuml
left to right direction

class Person {}

class Airline {}

Person "0..*" --- "0..*" Airline
```
```java
public class Student {
	public void play(Sport sport) {
		...
	}
}
```

- Aggregation:

```plantuml
left to right direction

class Airliner {}
class CrewMember {}
Airliner "0..*" o--- "0..*" CrewMember
```
```java
public class Airliner {
	private ArrayList<CrewMember> crew;

	public Airliner() {
		crew = new ArrayList<CrewMember>();
	}
	
	public void add(CrewMember crewMember) {...}
}
```

- Composition:

```plantuml
left to right direction
class House {}
class Room {}

House *--- "1..*" Room
```
```java
public class Human {
	private Brain brain;

	public Human() {
		brain = new Brain();
	}
}
```
- Inheritance:
```plantuml
class Animal {
	#numberOfLegs: int
	#numberOfTails: int
	#name: String
	+walk()
	+run()
	+eat()
}
class Dog extends Animal {
	+playFetch()
}
class Cat extends Animal {
	+playWithYarn()
}
```

- Interfaces:
```plantuml
interface IPublicSpeaking {
	+givePresentaion()
	+speak()
}
interface IPublicConversation {
	+lowerVoiceVolume()
	+speak()
}
class Person implements IPublicSpeaking, IPublicConversation {
	+speak()
}
```

### Assignment:

**Assignment Topic:**

_“Draw a UML class diagram of an Object-Oriented model for a car rental company that keeps track of cars, renters and renters renting cars ”_

Create a UML class diagram to represent this information. Showing the correct classes and relationships is enough. **Do not** add attributes or methods to the classes.

**Hint****:** You may want to make a class for "renters renting cars".

**Note****:** This is an ungraded assignment for practice. The goal is to help you get familiar with our assessments (Peer Review) in our system.

```plantuml
left to right direction
class CarRantalCompnay
class Car
class Renter
class Rental

CarRantalCompnay "1" o--- "0..*" Car
CarRantalCompnay "1" o--- "0..*" Rental
CarRantalCompnay "1" o--- "0..*" Renter

Car "1" ---o "1" Rental
Rental "0..*" o--- "1" Renter

```
![[Screen Shot 2023-11-18 at 11.37.24 AM.png]]
