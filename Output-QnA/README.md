## Javascript Output questions

<h4 align-item="center"><i>Reference: youtube > TechMentor Tutorials series > interview output series </i></h4>

### Question 1:

```javascript
function x() {
  // var i=1;
  for (var i = 1; i < 5; i++) {
    function callx(i) {
      setTimeout(function () {
        console.log(i);
      }, 1000);
    }
    callx(i);
  }
}

x();

//output: 5 (4 times)
/* 
Explaination: 

1. closure has lexical scope reference of i, so till i becomes 5 it will wait for 1 sec
2. Every function has global execution context



*/
```

<br/>
<hr/>
<br/>

### Question 2:

```javascript
//closure

/* function counter(){
    var count=0;
    return function increment(){
        count++;
        console.log(count);
    }
} 

var counter1 = counter();
counter1();
counter1();

//output: 1 2
*/

//using constructor
function Counter() {
  var count = 0;
  this.increment = function () {
    count++;
    console.log(count);
  };
  this.decrement = function () {
    count--;
    console.log(count);
  };
}

var counter1 = new Counter();
counter1.increment();
// counter1.decrement();

var counter2 = new Counter();
counter2.decrement();

// Here, value is taking from reference initially it is 1 then -1
// When new instance is created then new global execution context is created, so it will take new variable
```

<br/>
<hr/>
<br/>

### Question 3:

```javascript
// What will be the output

(function immediateA(a) {
  return (function immediateB(b) {
    console.log(a);
  })(1);
})(0);

/*
notes:
'a' scope is available in inner function.
*/
```

<br/>
<hr/>
<br/>

### Question 4:

```javascript
console.log(myVar);
console.log(myConst);
console.log(myLet);

var myVar = "value";
const myConst = 3.14;
let myLet = 10;

/**
 * Notes:
 * -  Due to hoisting var is declared at the top but not let, constant
 * -  for const, value should be assigned at the level of declaration.
 * -	const doesnt support hoisting
 * -	We cannot initialise the let and const
 * -	We can access var before initialisation but cant access let, const before initialisation.
 */
```

<br/>
<hr/>
<br/>

### Question 5:

```javascript
const len = 4;
const num = [];

for (var i = 0; i < len; i++);
{
  num.push(i + 1);
}

// len = 5;
console.log(len); //4
console.log(num); //[5]

/**
 * Notes:
 * -	cant re assign to const
 * -	As there is semicolon after for loop
 * -	If semicolon ir removed after for loop, then it is [1,2,3,4]
 */
```

<br/>
<hr/>
<br/>

### Question 6:

```javascript
function too() {
  let a = (b = 0);
  a++;
  return a;
}

console.log(too());
console.log(b);
console.log(a);

/*
Notes:
let a=b=0; Here a is declared with and b is not declared means it is var, b is global scope
so 'a' is not accessible outside, and 'b' is accessible outside

output:
1 0
a is not defined

*/
```

<br/>
<hr/>
<br/>

### Question 7:

```javascript
let a = [];
let b = [];
let c = new Date("1990");
let d = new Date("1990");
console.log(a == b);
console.log(a === b);
console.log(c == d);
console.log(c === d);

/*
Notes:
Here for array and Date, new memory is allocated 

Output:
false
false
false
false

*/
```

<br/>
<hr/>
<br/>

### Question 8:

```javascript
var a = 10;
(function () {
  console.log(a);
  var a = 11;
})();

/*
Notes:

In function block, variable will be hoisted
so
var a = undefined;
console.log(a);
a=11;


output:
undefined

*/
```

<br/>
<hr/>
<br/>

### Question 9:

```javascript
var c = 2;

function b(a) {
  return c;
}

// console.log(b());
console.log(b(10, 20));

/*
Notes:
-	It doesnt matter how many parameters we are sending, as the call method name should be same
-	As the 'c' variable is global scope, so 'c' is accessible inside function

Output:
2
*/
```

<br/>
<hr/>
<br/>

### Question 10:

```javascript
console.log("first");

setTimeout(function () {
  console.log("second");
}, 0);

console.log("third");

/*

Notes:
Here, setTimeout is vlocking event, which is block the event

Output:

first
third
second

*/
```

<br/>
<hr/>
<br/>

### Question 11:

```javascript
let foo = null;
console.log(typeof foo === "object");
console.log(typeof foo === "undefined");

/*

Notes:
typeof of null is object,
null is not value but it is object

Ouput:
true
false

*/
```

<br/>
<hr/>
<br/>

### Question 12:

```javascript
const myObject = {
  myMethod(items) {
    console.log(this);
    const callback = () => {
      console.log(this);
    };
    items.forEach(callback);
  }
};

myObject.myMethod([1, 2, 3]);

/*
Notes:
'this' refer to method reference here,
so 4 time method reference will be printed
*/
```

<br/>
<hr/>
<br/>

### Question 13:

```javascript
const obj = { a: "" };
obj.a = "shyam";
obj.a = "kumar";
console.log(obj.a);

/*
Notes:
Here, 

1. we are missing the object initiliasation,
it should be
const obj = {a: ""}


2. we cant access const obj like obj.a
it should be
obj.a

3. we cant access 'a' in console.log
it should be
console.log(obj.a)

*/
```

<br/>
<hr/>
<br/>

### Question 14:

```javascript
var A = {
  x: function () {
    console.log(x);
  },
  y: function () {
    console.log(y);
  }
};

A.x().y();

/*
Notes:
-	Here, x is called in console, but x is not called like a function x(), but x, it means it is variable, but it is not defined,
so will give an error. x is not defined
-	

Output:
x is not defined

*/
```

<br/>
<hr/>
<br/>

### Question 15:

```javascript
var a = { x: 1 };
var b = { x: 1 };
console.log(a === b);
console.log(a == b);

/*

Notes:

a and b both are object
object treat difference reference which cant be same value.


Ouput:

false
false

*/
```

<br/>
<hr/>
<br/>

### Question 16:

```javascript
var c = { x: 1 };
d = c;
d.x = 3;
console.log(c);
console.log(d);

/*
Notes:

It is an example of shallow copy.

Here, c & d are objects
c reference is given to d, 
so the change in d reflects changes in d

Output:
{x:3}
{x:3}


*/
```

<br/>
<hr/>
<br/>

### Question 17:

```javascript
function num(a, b, a) {
  console.log(a, b, a);
}
num(1, 2, 3);

/*
Notes:
'a' parameter is passed twice
the first 'a' is replced with last 3 value

Output:
3 2 3

*/
```

<br/>
<hr/>
<br/>

### Question 18:

```javascript
function xyz(x, y, ...args) {
  let sum = 0;
  args.forEach((value) => {
    sum += value; //0+3=3+4=7+5=12
  });
  console.log(sum); //12
}

xyz(1, 2, 3, 4, 5);
xyz(1, 2);

/*

Notes:
here
1,2 will go in x,y and rest 3,4,5 will go in args, so
sum += value;//0+3=3+4=7+5=12
for 2nd case, x=1,y=2, but no value for args, so sum is 0.

Output:
12 0 

*/
```

<br/>
<hr/>
<br/>

### Question 19:

```javascript
const colorConfig = {
  red: true,
  blue: false,
  green: true,
  black: true,
  yellow: false,
  white: false
};

const colors = ["pink", "red", "blue"];
console.log(colorConfig.colors[1]);

/*
Notes:
As 'colorConfig' object doesnt have colors property, so it will give undefined --> value of undefined of 1 gives an error.

Output:
can not read property of undefined


*/
```

<br/>
<hr/>
<br/>

### Question 20:

```javascript
const user = {
  firstname: "Ram",
  lastname: "singh",
  status: true
};

const { status, ...userDetails } = user;
console.log(userDetails);

/*

Notes:
const {status, ...userDetails} = user;
Here it is called object destructing, ... it is rest parameter 
status have status value but userDetails gets the remaining values.

Output:
{
	firstname: 'Ram',
	lastname: 'singh',
}

*/
```

<br/>
<hr/>
<br/>

//============
