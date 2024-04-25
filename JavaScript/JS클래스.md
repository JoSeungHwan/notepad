# prototype

```javascript
const fruits = [‘Apple’, ‘Banana’, Cherry’]
const fruits - new Array(‘Apple’, ‘Banana’, ‘Cherry’)

console.log(fruits) Apple Banana Cherry
console.log(fruits.length) 3
console.log(fruits.includes(‘Banana’)) turn
console.log(fruits.includes(‘Orange’)) false

Array.prototype.Jo = function () {
  console.log(this)	Apple Banana Cherry
}
fruits.Jo()
const arr = []	[]
arr.Jo()

const Jo = {
  firstName: ‘Jo’,
  lastName: ‘hh’,
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}
const neo = {
  firstName: ‘Neo’.
  lastName: ‘hh’
}
console.log(Jo.getFullName())	Jo hh
console.log(neo.getFullName())		Neo hh
console.log(Jo.getFullName.call(neo))	Neo hh

function User(first, last) {
  this.firstName = first
  this.lastName = last
}
User.prototype.getFullName = function () {
  return `${this.firstName} ${this.lastName}`
}
const jo = new User(‘Jo’, ‘hh’)
const neo = new User(’Neo’, ‘hh’)
console.log(jo)	Jo hh
console.log(neo)	Neo hh
console.log(jo.getFullName())	Jo hh
console.log(neo.getFullName())		Neo hh
```

# ES6 Class 기본문법

```javascript
function User(first, last) {
  this.firstName = first
  this.lastName = last
}
User.prototype.getFullName = function () {
  return `${this.firstName} ${this.lastName}`
}
const jo = new User(‘Jo’, ‘hh’)
const neo = new User(‘Neo’, ‘hh’)
console.log(jo.getFullName()) 	Jo hh
console.log(neo,grtFullName()) 		Neo hh

class User {
  constructor(first, last) {
    this.firstName = first
    this.lastName = last
  }
  getFullName() {
    return `${this.firstName} ${this.lastName}`
  }
}
const jo = new User(‘Jo’, ‘hh’)
const neo = new User(‘Neo’, ‘hh’)
console.log(jo.getFullName()) 	Jo hh
console.log(neo,grtFullName()) 		Neo hh
```

# Getter, Setter

## Getter : 값을 조회할때

## Setter : 값을 할당할때

```javascript
class User {
	constructor(first, last) {
		this.firstName = first
		this.lastName = last
		this.fullName = `${first} ${last}`
	}
}
const jo = new User(‘Jo’, ‘hh’)
console.log(jo) 	firstName: Jo		lastName: hh		fullName: Jo hh
jo.firstName = ‘Neo’
console.log(jo)	firstName: Neo		lastName: hh		fullName: Jo hh 	fullName은 안바뀜

class User {
	constructor(first, last) {
		this.firstName = first
		this.lastName = last
	}
	getFullName() {
		return `${this.firstName} ${this.lastName}`
	}
}
const jo = new User(‘Jo’, ‘hh’)
console.log(jo.getFullName())	Jo hh
jo.firstName = ‘Neo’
console.log(jo.getFullName())	Neo hh

Getter과 Setter를 사용해서 바꿔보자
class User {
  constructor(first, last) {
    this.firstName = first
    this.lastName = last
  }
  get fullName() {		Getter설정
    return `${this.firstName} ${this.lastName}`
  }
  set fullName(value) {		Setter설정
    console.log(value)	Neo Jo
    ;[this.firstName, this.lastName] = value.split(‘ ‘)
  }
}
const jo = new User(‘Jo’, ‘hh’)
console.log(jo.fullName)	Jo hh	Getter설정
jo.firstName = ‘Neo’
console.log(jo.fullName)	Neo hh	Getter설정

jo.fullName = ’Neo Jo		Setter설정
console.log(jo) 	Neo Jo
```

# 정적 메소드

```javascript
class User {
  constructor(first, last) {
    this.firstName = first
    this.lastName = last
  }
  get fullName() {
    return `${this.firstName} ${this.lastName}`
  }
  static isUser(user)	{	정적 메소드 설정
    is (user.firstName && user.lastName) {
      return true
    }
    return false
  }
}
const jo = new User(‘Jo’, ‘hh’)
const neo = new User(‘Neo’, ‘ss’)
const lewis = {
	name: ‘sh’,
	age: 29
}
console.log(jo.getFullName())	Jo hh
console.log(neo.getFullName())		Neo ss
console.log(User.isUser(jo))	trun
console.log(User.isUser(neo))	trun
console.log(User.isUser(lewis))		false
```

# 상속과 instanceof

```javascript
//운송수단
class Vehicle {
  constructor(acceleration =1) {
    this.speed = 0
    this.acceleration = acceleration
  }
  accelerate() {
    this.speed += this.acceleration
  }
  decelerate() {
    is (this,speed <= 0) {
      console.log(‘정지’)
      return
    }
    this,speed -= this.acceleration
  }
}

//자전거
class Bicycle extends Vehicle {
  constructor(price = 100, acceleration) {
    super(acceleration)
    this.price = price
    this.wheel = 2
  }
}
const bicycle = new Bicycle(300, 2)
console.log(bicycle)	Bicycle {speed: 0, acceleration: 2, price: 300, wheel: 2}
const bicycle = new Bicycle(300)
console.log(bicycle)	Bicycle {speed: 0, acceleration: 1, price: 300, wheel: 2}
console.log(bicycle instanceof Bicycle)	true
console.log(bicycle instanceof Vehicle)	true
instanceof 상속 확인
//자동차
class Car extends Bicycle {
  constructor(license, price, acceleration) {
    super(price, acceleration)
    this.license = license
    this.wheel = 4
  }
  accelerate() {
    if (!this.license) {
      console.error(‘무면허’)
      return
    }
    this.speed += this.acceleration
    console.log(‘가속’, this.speed)
  }
}
const carA = new Car(true, 7000, 10)
const carB = new Car(false, 4000, 6)
console.log(carA)		Car {speed: 0, acceleration: 10, price: 7000, wheel: 4, license = true}
console.log(carB)		Car {speed: 0, acceleration: 6, price: 4000, wheel: 4, license = false}

//보트
class Boat extends Vehicle {
  constructor(price, acceleration) {
    super(acceleration)
    this.price = price
    this.motor = 1
  }
}
const boat = new Boat(10000, 5)
console.log(boat)		Boat {speed: 0, acceleration: 5, price: 10000, motor: 1}
```

# instanceof와 constructor

```javascript
class A {
  constructor() {}
}
class B extends A {
  constructor() {
    super()
  }
}
class C extends B {
  constructor() {
    super()
  }
}
const a = new A()
const b = new B()
const c = new C()

console.log(a instanceof A)   true
console.log(a instanceof B)   false
console.log(a instanceof C)   false

console.log(b instanceof A)   true
console.log(b instanceof B)   true
console.log(b instanceof C)   false

console.log(c instanceof A)   true
console.log(c instanceof B)   true
console.log(c instanceof C)   true

console.log(c.constructor === A)    false
console.log(c.constructor === B)    false
console.log(c.constructor === C)    true


const fruits = [‘Apple’, ‘Banana’]
const fruits = new Array(‘Apple’, ‘Banana’)

console.log(fruits.constructor === Array)   true
```
