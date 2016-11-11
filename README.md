

# Declarative Style V.S. Imperative Style

> :heart: A programmer’s dream is to write code, 
and be able to re-use it with little effort!

:thumbsup: Code that can be repeatedly used with little effort

:thumbsup: Code that can be tested easily

:thumbsup: Code that can express themself

--------------------------------------------------------



# Let's Try!

```javascript
var fruits = [
	{ name: 'apple',  price: 5 }, 
	{ name: 'orange', price: 10 }, 
	{ name: 'lemon',  price: 15 }
]
```

> **Get Sum Of Fruit Price**
```javascript
request('magicURL')
	.then((fruits)=>{
		// Your Code ...
	})
	.then((result)=>{
		console.log(result) // return 30
	})
```

--------------------------------------------------------


> **(Imperative Style)**

```javascript
request('magicURL')
	.then((fruits)=>{
		fruits
			.map((fruit)=fruit.price)
			.reduce((acc, price)=>acc+=price,0)
	})
	.then((result)=>{
		console.log(result) // 30
	})
```
--------------------------------------------------------


> **(Declarative Style)**

```javascript
request('magicURL')
	.then(selectKeyOf('price'))
	.then(priceMethod('sum'))
	.then((result)=>{
		console.log(result) // 30
	})
```
--------------------------------------------------------


## The difference between Imperative Style and Declarative Style?

> **Imperative Style** -> You told computer "How" to do it

> **Declarative Style** -> You told computer "What" to do




## Let's Get Dirty!

```javascript
var students = [
	{name: 'cw',    age: 27, gender:'M', allowance: 1000, department:'IT', 	  salary: 60000.56},
	{name: 'ken',   age: 31, gender:'M', allowance: 2000, department:'IT',    salary: 44000.32},
	{name: 'ck',    age: 35, gender:'M', allowance: 3000, department:'IT',    salary: 55000.11},
	{name: 'Ting',  age: 22, gender:'F', allowance: 4000, department:'sales', salary: 70000.85},
	{name: 'Linda', age: 27, gender:'F', allowance: 3000, department:'sales', salary: 40000.49}
]

// Pretended AJAX call from third party API
var whenDataLoaded = New Promise((resolve, reject)=>{
	resolve(students)
})

// then you have fake API call by ...
whenDataLoaded
	.then((result)=>{
		console.log(result) // Students Array
	})
```
--------------------------------------------------------


> **Stduent Age Average**

```javascript
var goal = 28.4 // Stduent Age Average

whenDataLoaded
	.then(selectObjKeyOf('age'))
	.then(priceMethod('average'))
	.then((result)=>{
		console.log(result === goal) // return true
	})
```
--------------------------------------------------------
	

> **Average IT's Salary**

```javascript
var goal = 53000
whenDataLoaded
	.then(getDepartmentOf('IT'))
	.then(selectObjKeyOf('salary'))
	.then(priceMethod('average'))
	.then(showDecimalsPoint(0))
	.then((result)=>{
		console.log(result === goal) // return true
	})
```

--------------------------------------------------------



> **Get Female only, display Name and Allowance**

```javascript
var goal = [ 
	{ name: 'Ting', allowance: 9000 },
	{ name: 'Linda', allowance: 8000 } 
]

whenDataLoaded
	.then(getGenderOf('F'))
	.then(addAllowance(5000))
	.then(removeObjKeyOf('gender'))
	.then(removeObjKeyOf('department'))
	.then(removeObjKeyOf('age'))
	.then(removeObjKeyOf('salary'))
	.then((result)=>{
		console.log(result === goal) // return true
	})
```

--------------------------------------------------------


> Please check out test folder to see how I implement the code above
,if there is something that is not clear, or you want me to 
explain more about it. Please email me at chaoweichiu@gmail.com


> This topic was inspired by [Real World Currying of JavaScript Functions](https://www.youtube.com/watch?v=fvJ9yWqXcZI)
and [Why Curry Helps](https://hughfdjackson.com/javascript/why-curry-helps/).


## About me

> :fire: Full Stack Web Developer

I am a freelance full-stack web developer, and I get so 
excited whenever there is a chance that I can challenge
myself and become a better software developer.


> :fire: Test Nerd

Few months age, I have exposed to TDD(test-driven development) way
of writing a software. Since then, I have fallen in love with that.
I was inspired by [MPJ](https://www.youtube.com/watch?v=TWBDa5dqrl8)
and [his video](https://www.youtube.com/watch?v=vqAaMVoKz1c)


------------------------------------------


## Extra Link

> [Custom Real World Functions](https://github.com/CHAOWEICHIU/ccw-custom-functions)

```javascript
decimalPlaces('.05') 	  		 // return 2
toTitleCase('hoW aRe yOU') 		 // return 'How Are You'
truncateString("how are you", 5) // return how a ...
validZipcode('48326')   		 // return true
// More ...
```