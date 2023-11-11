
![[software_requirements.png]]
**Requirement**:
- Requirement is determining what customer want, and it is a big part of building a software system.
- A user story is simply a requirement often in the perspective of an end-user and its look like :
	- As a ____, i want to ____ so that _____.
	- after this you can apply object-oriented thinking.
	- example:
		- _As an_ **online shopper**_, I want to add an_ _**item**_ _to my_ _**shopping cart**__, so that I can purchase it._
			- The nouns correspond to objects. So in this example we have identified three objects
		- _As an online shopper, I want to_ _**add**_ _an item to my shopping cart, so that I can_ _**purchase**_ _it._
			- The verbs can help identify the requirements that your objects might have.

**Categories of Objects in Design**
organizing software into these objects will allow the code to be more flexible, reusable, and maintainable:
- Entity : they correspond to some real-world entity.
- Boundary: objects that sit between systems. like object that deals with getting data from the internet.
- Control: responsible for coordination. like #mediator it simply coordinates the activities of other objects so that can stay loosely coupled.

**Record, Organize, and Refine Components**
- CRC: Class Responsibility Collaborator
- 