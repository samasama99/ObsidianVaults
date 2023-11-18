_Draw a UML class diagram
car rental company
that keeps track of cars, 
renters 
and renters renting cars_

```plantuml
left to right direction
class CarRentalCompany {}
class Car {}
class Renter {}
CarRentalCompany o--- "0..*" Car
Car "0..*" ---o Renter
```

form chat gpt:

```plantuml
left to right direction
class CarRentalCompany {
  -name: String
  -location: String
  -cars: List<Car>
  -renters: List<Renter>
  +addCar(car: Car): void
  +removeCar(car: Car): void
  +addRenter(renter: Renter): void
  +removeRenter(renter: Renter): void
  +getAvailableCars(): List<Car>
  +rentCar(car: Car, renter: Renter): void
  +returnCar(car: Car): void
}

class Car {
  -make: String
  -model: String
  -year: int
  +getMake(): String
  +getModel(): String
  +getYear(): int
}

class Renter {
  -name: String
  -age: int
  +getName(): String
  +getAge(): int
}

CarRentalCompany "1" o--- "*" Car
Car "0..1" o--- "0..1" Renter
```

```plantuml

left to right direction
class CarRentalCompany

class Car

class Renter

CarRentalCompany "1" o--- "*" Car
Car "0..1" --- "1" Renter
Renter "1" o--- "*" Car

```

```plantuml
left to right direction
class CarRentalCompany

class Car

class Renter

CarRentalCompany "1" o-- "*" Car
Car "0..1" --- "0..1" Renter
```
