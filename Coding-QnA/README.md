## Javascript Output questions
<h4 align-item="center"><i>Reference: youtube > TechMentor Tutorials series > interview programs </i></h4>

### Question 1:

```javascript
// Question1: Program to reverse each word in the given string

function reverse(str, substring) {
  return str.split(substring).reverse().join(substring);
}

let str = "bye sarfaraz";
let str1 = reverse(str, "");
let str2 = reverse(str1, " ");

console.log(str2);

/*
Notes:

-	Better to use javascript methods
-	Here, we are revering the whole string then combining --> then diving the tring with space then reverse it.

Output:
bye sarfaraz --> eyb zarafras

*/
```

<br/>
<hr/>
<br/>

### Question 2:

```javascript
//Question 2: Anagram, Given 2 strings, return true if they are anagram of one another.
//Example: Mary is an anagram of army

//algo
//count the words

function common(str) {
  return str.toLowerCase().split("").sort().join("");
}
let str1 = "Mary";
let str2 = "Army";

let one = common(str1);
let two = common(str2);
let isAnagram = one === two ? true : false;
console.log(isAnagram);

/*
Notes:
Anagram means, position may be different but the word should be same.

-	
-	

Output:
Mary --> Army


*/
```

<br/>
<hr/>
<br/>

### Question 3:

```javascript
//Question 3: Fabonacci series

//variables
let n1 = 0;
let n2 = 1;
let n3;
let limit = 10;

let arr = [n1, n2];

for (let i = 0; i < limit; i++) {
  n3 = n1 + n2;
  n1 = n2;
  n2 = n3;
  //push n3 in arr
  arr.push(n3);
}

console.log(arr.join(","));

/*
Notes:

-	Algo:
-	initial 2 values are 0,1 then sum of last 2 numbers is next value till limit
-	last number should be 1st number, result should be second number

Output:
0,1,1,2,3,5,8,13,21,34,55, 89


*/
```

<br/>
<hr/>
<br/>

### Question 4:

```javascript
let inputNum = 153;
let sum = 0;
let temp = inputNum;

while (temp > 0) {
  //will give remaining value 153%10=3
  let reminder = temp % 10;
  sum = sum + reminder ** 3; //or y cube=(reminder*reminder*reminder);
  temp = parseInt(temp / 10); // 153/10= 15
}

// console.log(inputNum, sum);

if (inputNum == sum) {
  console.log("Yes! Amstrong number");
} else {
  console.log("Not! Amstrong number");
}

/*
Notes:
Armstrong number
-	It is the number which is equal to sum of cubes of its digits
-	Example: 0,1,153,370,371 and 407 are armstrong numbers

153 = (1*1*1) + (5*5*5) + (3*3*3)
=1 + 125 + 27
=153

Output:
yes


*/
```

<br/>
<hr/>
<br/>

### Question 5:

```javascript
//Question 5: Factorial number

function factorial(inputNum) {
  let result = 1;
  for (let i = inputNum; i >= 1; i--) {
    result = result * i;
  }
  return result;
}

console.log(factorial(5));

/*

Notes:

Factorial number
-	5! = 5*4*3*2*1 = 120
-	3! = 3*2*1 = 6

Output:
120

*/
```

<br/>
<hr/>
<br/>

### Question 6:

```javascript
//Question 6: Swapping string variables without temporary/third variables

/* 

//using 3rd variable
function strSwap(str1, str2){
	let temp = str1;
	str1 = str2;
	str2 = temp;
	return [str1, str2].join(",")
} 

console.log(strSwap("hi","bye"));
*/

function strSwap(str1, str2) {
  //Array destructuring
  [str2, str1] = [str1, str2];
  console.log(str1, str2);
}

strSwap("hi", "bye");
```

<br/>
<hr/>
<br/>

### Question 7:

```javascript
// Question 7: Palindrome number

function isPalindrome(inputNum) {
  let result = inputNum.split("").reverse().join("");
  return result == inputNum
    ? console.log("Palindrome")
    : console.log("Not a palindrome");
}

isPalindrome("131");

/*
Notes:
Palindrome number
-	A number that is same after reverse
-	Example: 48984, 131, 545, abcba

Output:
Palindrome or not

*/
```

<br/>
<hr/>
<br/>

### Question 8:

```javascript
//Question 8: Remove duplicates from an array without using loops

function removeDuplicate(arr) {
  // let mySet = new Set(arr);
  // return [...mySet];//converting set into array

  return [...new Set(arr)];
}
console.log(removeDuplicate([1, 1, 2]));
```

<br/>
<hr/>
<br/>

### Question 9:

```javascript
/*

Given:
Add index of arr1[i] + arr2[i] and create new output array
let arr1 = [0,1,2,4,1,3,5]
let arr2 = [5,6,7,2,1,5,8]
ouput 	 = [5,7,9,6,2,8,13]

*/

let arr1 = [0, 1, 2, 4, 1, 3, 5];
let arr2 = [5, 6, 7, 2, 1, 5, 8];

let arr3 = arr1.map((value, index) => value + arr2[index]);
console.log(arr3);

/*
Notes:

-	We will add index of 1st and index of 2nd and give the 3rd array	

Output:

[5,7,9,6,2,8,13]

*/
```

<br/>
<hr/>
<br/>

### Question 10:

```javascript
// Question 10: Program to find one array values count in another array in javascript

/*
Given: 
let arr1 = [3,4,5,6,5,4,5]
let arr2 = [2,3,4,5,6]

*/
let arr1 = [3, 4, 5, 6, 5, 4, 5];
let arr2 = [2, 3, 4, 5, 6];

let arr3 = arr2.map((value2) => {
  let total = arr1.reduce((count, value1) => {
    if (value2 == value1) count++;
    return count;
  }, 0);
  return `${value2}: ${total}`;
});

console.log(arr3);

/*
Notes:

2:0 --> means, 2 is the element of arr2 and 0 is how many times 2 is repeating in arr1.

- How many time arr2 values are coming in arr1	
-	Need to calculate the count, so need to use reduce
-	if(value2 == value1) count++; It means, value of arr1 is equal to value of arr2 then increment the count
Output:
['2:0','3:1','4:2','5:3','6:1']


*/
```

<br/>
<hr/>
<br/>

### Question 11:

```javascript
// Question 11: Program to convert nested object into flat object

let student = {
  name: "Sarfaraz",
  address: {
    personal: {
      city: "Nanded",
      pincode: 431602
    },
    office: {
      city: "Hyderabad",
      pincode: 500089
    }
  }
};

//Output Expected
let output = {
  student_name: "Sarfaraz",
  student_address_personal_city: "Nanded",
  student_address_personal_pincode: 431602,
  student_address_office_city: "Hyderabad",
  student_address_office_pincode: 500089
};

let outputObj = {};

let recursive = (obj, name) => {
  for (let key in obj) {
    if (typeof obj[key] == "object") {
      //when it is object
      recursive(obj[key], name + "_" + key);
    } else {
      outputObj[name + "_" + key] = obj[key];
    }
  }
};

recursive(student, "student"); //as student keyword is added
console.log(outputObj);
/*
Notes:

-	
-	

Output:



*/
```

<br/>
<hr/>
<br/>

### Question 12:

```javascript
//Question 12: Program to write a function for add(a)(b)(c) to get addition of all

/* let add =(a)=>{
	return (b)=>{
		return (c)=>{
			return a+b+c;
		}
	}
} */

//using recursion
let add = (a) => {
  return (b) => {
    //if the value of b exist then add a+b otherwise return a
    return b ? add(a + b) : a;
  };
};

console.log(add(1)(2)(3)());

/*
Notes:

-	
-	

Output:



*/
```

<br/>
<hr/>
<br/>

### Question 13:

```javascript
// Question 13: Program to convert multi dimention array into single array

/*
Given:

let arr = [1,[2,3],[[4,5,6]],[[[7,8,9,10]]]]
output: [1,2,3,4,5,6,7,8,9,10]

*/

let newArr = [];

function multToSingleArr(arr) {
  arr.forEach((value) => {
    //if my value is array than call the recursive function otherwise push to new array
    if (Array.isArray(value)) {
      multToSingleArr(value);
    } else {
      newArr.push(value);
    }
  });
}

let arr = [1, [2, 3], [[4, 5, 6]], [[[7, 8, 9, 10]]]];

multToSingleArr(arr);
console.log(newArr);

/*
Notes:

- if my value is array than call the recursive function otherwise push to new array	
-	

Output:



*/
```

<br/>
<hr/>
<br/>

### Question 14:

```javascript
//Question 14: Program to sort only positive numbers of the array

let arr = [-1, 40, 20, -4, 10, 2, 70, -2, 6, 9];
//ouput: [-1,2,6,-4,9,10,20,-2,40,70]

function postiveSortArr() {
  let sortedPositiveArr = arr.filter((item) => item > 0).sort((a, b) => a - b);
  // console.log(sortedPositiveArr);

  let sortedArr = [];

  let j = 0;

  for (let value of arr) {
    if (value > 0) {
      //if positive then push in sorted array
      sortedArr.push(sortedPositiveArr[j++]);
    } else {
      //if -ve value then as it is
      sortedArr.push(value);
    }
  }
  return sortedArr;
}

console.log(postiveSortArr(arr));

/*
Notes:
Here
-	-ve values are not changed but only +ve numbers will sort
-	

Output:



*/
```

<br/>
<hr/>
<br/>

### Question 15:

```javascript
// Questions 15: Remove duplicate keys and merge values of an object

let originalArr = [
  {
    id: 1,
    elements: [1, 2]
  },
  {
    id: 1,
    elements: [3, 4]
  },
  {
    id: 2,
    elements: ["a", "b"]
  },
  {
    id: 2,
    elements: ["c"]
  },
  {
    id: 3,
    elements: ["a2b"]
  }
];

// console.log(originalArr);

// function removeDuplicateAndMerge(originalArr) {
//   let reducedArr = originalArr.reduce((obj, item) => {
//     if (obj[item.id]) {
//       obj[item.id].elements.push(...item.elements);
//     } else {
//       obj[item.id] = { elements: [...item.elements] };
//     }
//     return obj;
//   }, {});
//   return reducedArr;
// }

// let res = removeDuplicateAndMerge(originalArr);
// console.log(Object.values(res));

//---------- using forEach & find
let mergedArr = [];

originalArr.forEach((obj) => {
  let existingObj = mergedArr.find((item) => item.id === obj.id);

  if (existingObj) {
    existingObj.elements = existingObj.elements.concat(obj.elements);
  } else {
    mergedArr.push(obj);
  }
});

console.log(mergedArr);

/*
Notes:

-	
-	

Output:
let originalArr = [
	{
		id:1,
		elements: [1,2,3,4]
	},
	{
		id:2,
		elements: ['a','b','c']
	},
	{
		id:3,
		elements:['a2b']
	}
]


*/
```

<br/>
<hr/>
<br/>

### Question 16:

```javascript
// Question 16: Program to shift zero at last in an array

let arr = [1, 0, 2, 3, 0, 7, 9, 0, 10];

//using filter
/* function shiftZeroAtLast(arr) {
  let nonZeroArr = arr.filter(item => item !== 0);
  let zeroArr = arr.filter(item => item === 0);
  return nonZeroArr.concat(zeroArr);
} */

//using for loop
function shiftZeroAtLast(arr) {
  for (let i = arr.length - 1; i >= 0; i--) {
    if (arr[i] == 0) {
      arr.splice(i, 1);
      arr.push(0);
    }
  }
  return arr;
}

console.log(shiftZeroAtLast(arr));

/*
Notes:

-	While solving with for loop, loop it reverse
-	if we find 0 then delete the element and insert at the lasst.	

Output:
[1,2,3,7,9,10,0,0,0]


*/
```

<br/>
<hr/>
<br/>

### Question 17:

```javascript
//Question 17: Program to fetch student object whose marks average is greater then other students

let students = [
  {
    name: "Virat Kohli",
    marks: [70, 60, 80, 65, 90]
  },
  {
    name: "Rohit Sharma",
    marks: [80, 62, 70, 75, 81]
  },
  {
    name: "KL Rahul",
    marks: [81, 67, 72, 69, 84]
  },
  {
    name: "Jaspreet Bumrah",
    marks: [74, 69, 83, 60, 92]
  }
];

//--- ouput
let output = {
  name: "Jaspreet Bumrah",
  marks: [74, 69, 83, 60, 92]
};

let reducedArr = students.reduce(
  (obj, item) => {
    let total = item.marks.reduce((sum, mark) => {
      return sum + mark;
    }, 0);

    let average = total / item.marks.length;

    return obj.count < average ? { row: item, count: average } : obj;
  },
  { row: {}, count: 0 }
);

console.log(reducedArr);

/*
Notes:

-	
-	

Output:



*/
```

<br/>
<hr/>
<br/>

### Question 18:

```javascript
//Question 18: Reverse a string without inbuild method

// Using inbuilt methods
/* function reverseString(str){
	return str.split("").reverse().join("");
} */

function reverseString(str) {
  let reverseStr = "";
  for (let i = str.length - 1; i >= 0; i--) {
    reverseStr = reverseStr + str[i];
  }
  return reverseStr;
}

let str = "India";
console.log(reverseString(str));

/*
Notes:

-	
-	

Output:



*/
```

<br/>
<hr/>
<br/>

### Question 19:

```javascript
//Question 19: Print 1 to 5 number in every second

let i = 1;
let interval = setInterval(function () {
  console.log(i++);
}, 1000);

setTimeout(function () {
  clearInterval(interval);
}, 5000);
```

<br/>
<hr/>
<br/>

### Question 20:

```javascript
//Question 20: Program to return odd repeating values of an array.
//input: ['a','b','a','b','c','a','c','d']
//ouput: ['a:3','d:1']

function oddArray(arr) {
  let result = arr.reduce((obj, value) => {
    if (obj[value]) {
      obj[value]++;
    } else {
      obj[value] = 1;
    }
    return obj;
  }, {});

  return result;
}

let arr = ["a", "b", "a", "b", "c", "a", "c", "d"];

let finalresult = Object.entries(oddArray(arr))
  .filter((item) => {
    return item[1] % 2 != 0;
  })
  .map((item) => {
    return item[0] + ":" + item[1];
  });
console.log(finalresult);
```

<br/>
<hr/>
<br/>

### Question 21:

```javascript
//Question 21: Same key value put together in an array

let input = [
  { type: "ABC", value: 123 },
  { type: "XYZ", value: 456 },
  { type: "ABC", value: 789 }
];

let output = {
  ABC: [123, 789],
  XYZ: [456]
};

let reducedArr = input.reduce((obj, item) => {
  //if in accoumulator(obj) type is not present --> set the blank array --> otherwise push the value
  if (!obj[item.type]) {
    obj[item.type] = [];
  }
  obj[item.type].push(item.value);
  return obj;
}, {});

console.log(reducedArr);

/*
Notes:

-	When keys are same then its values should come together

Output:

{
	"ABC" : [123, 789],
	"XYZ" : [456]
}

*/
```

<br/>
<hr/>
<br/>

### Question 22:

```javascript
//Question 22: Remove duplicate from an array without inbuild function

let duplicate = [1, 2, 3, 2, 3];

let uniqueArr = [];

for (let value of duplicate) {
  //check if the value exists using indexOf

  //using indexOf
  /* if(uniqueArr.indexOf(value) === -1){
		uniqueArr.push(value);
	} */

  //using includes
  if (!uniqueArr.includes(value)) {
    uniqueArr.push(value);
  }
}

console.log(uniqueArr);
```

<br/>
<hr/>
<br/>

### Question 23:

```javascript
//Question 23: Program to find max sum of chunk of array

let input = [10, 4, 19, 2, 18, 5, 9, 2, 19, 9, 10, 2];
let size = 4;

let count = 0;
let max = 0;
let j = 1;

for (let i of input) {
  count += i;

  //if j is equal to siz then --> check count is less then count --> assign count into max othersie assign - to j and count
  if (j == size) {
    console.log(max + "<" + count);
    if (max < count) {
      max = count;
    }
    j = 0;
    count = 0;
  }
  j++;
}

console.log(max);

/*
Notes:
Here,
-	We need to add first 4 values means sum first 4
-	Get the maximum sum and show

Output:
40

*/
```

<br/>
<hr/>
<br/>

<h4 align-item="center"><i>Reference: youtube > still learning series > interview question</i></h4>


## Javascript Interview questions

<br/>
<hr/>
<br/>

### Question 1:

```javascript
//Question 1: What is flat method

const multiArr = [3,5,[4,5],6,[3,5,[5,[6,[7]]]]];

console.log(multiArr.flat(Infinity));

```

<br/>
<hr/>
<br/>

### Question 2:

```javascript
//Question 2: Print numbers from 1 t0 10 using for loop

for(let i=1;i<=10;i++){
	console.log(i);
}

// Print 2 table
for(let i=1;i<=10;i++){
	console.log(2*i);
}

```

<br/>
<hr/>
<br/>

### Question 3:

```javascript
// Question 3: Printing number from 1 to 10 using without loop

function count(start, end){
	console.log(start);
	if(start < end){
		count(start + 1, end);
	}
	return
}

count(1, 10);

```

<br/>
<hr/>
<br/>

### Question 4:

```javascript
//Question 4: Sum of array values


let arr = [1,2,3,4,5]

const sum = arr.reduce((accumulator, currntVal)=>{
	return accumulator + currntVal;
})

console.log(sum);


//Explaination: reduce will reduce the value
```

<br/>
<hr/>
<br/>

### Question 5:

```javascript
//Question 5: How to add the value in array at specific position



//Example 1: Inserting 
let arr = ['jan','feb','apr','may']
arr.splice(2,0,'mar');
console.log(arr);

//Example: Updating or modiying
let arr1 = ['jan','feb','narch', 'apr','may']
arr1.splice(2,1,'mar');
console.log(arr1);

//Example: Removing
let arr2 = [ 'jan', 'feb', 'feb', 'mar', 'apr', 'may' ]
arr2.splice(2,1);
console.log(arr2);

/*
Explaination:

splice(2,0,'mar');
-	It means, add at the 2nd position, delete 0 element, add 'mar' value
-	splice() update the original array
-	In Exmaple 2, 1 indicate the value to be deleted.

*/
```

<br/>
<hr/>
<br/>

### Question 6:

```javascript
//Question 6: Find the 2nd largest number in an array

let arr = [80, 57, 29, 2, 62, 3]
arr.sort((a,b)=> a-b);
console.log(arr[arr.length-2]);

/*
Notes:

arr.sort((a,b)=> a-b);
here, sort() will not properly, so we pass the 2 parameters a, b to get the proper sorting
*/
```

<br/>
<hr/>
<br/>

### Question 7:

```javascript
// Question 7: Difference between map & filter function

// map function
let arr1 = [1,2,3,4,5];

const arr2 = arr1.map((val)=>{
	return val + 3
})

console.log(arr2);

//--------------

//filter: Gives value greater than 3
const filteredArr = arr1.filter((val)=>{
	return val > 3;
})
console.log(filteredArr);

//-------------- using array object
//Filter the values equal to 30
const obj = [
	{
		name: "Rohit Sharma",
		age: 36,
	},
	{
		name:"Ishant Kishan",
		age: 25
	},
	{
		name: "Hardik Pandya",
		age: 28
	},
	{
		name: "KL Rahul",
		age: 30
	}
]


const newArr = obj.filter(item=>{
	return item['age'] === 30;
})

console.log(newArr);

/*
Notes:

-	map & filter function almost same with slight difference
-	map() will print the value 1 by 1
-	filter() will filter the array based on the condition

*/
```

<br/>
<hr/>
<br/>

### Question 8:

```javascript
//Question 8: Mobile & Email validation

//Scenario:
/*
number should be 10
no alphabetic number allowed, means Not a number check
*/

let mobile = '9876543210';

if(mobile.length === 10 && !isNaN(mobile)){
	console.log(`valid mobile number`);
}else{
	console.log(`mobile number is not valid`);
}

let email = "test@gmail.com"
if(email.includes("@") && email.includes(".")){
	console.log(`Valid email`);
}else{
	console.log(`Not a valid email`);
}
```

<br/>
<hr/>
<br/>

### Question 9:

```javascript

//Question 9: Difference between var, let and const

function funOne(){
	if(2===2){
		var a = 10;
		const b = 20;
	}
	console.log(a);
	// console.log(b);
}
funOne();


x = 8;
console.log(x);
var x;
// let x;


//-------- Redeclaration -------------
var a = 5;
var a = 10;
console.log(a);

/* let cc = 5;
let cc = 10;
console.log(cc); */

/* const dd = 4;
const dd = 10;
console.log(dd); */


//----------- Reassign
let aa = 5;
aa = 6;
console.log(`Reassign: ${aa}`);

var dd = 5;
dd =10;
console.log(`Reassing: ${dd}`);

/*
Notes:

1. Scope: 
-	var is functional scope, let, const is block scope
- {} inside curly bases it is called block scope. 
- after the- function {} it is called function scope.

2. Hoisting:
-	only var is hoisted, where var is declared at the top --> than initilation --> than usage.

3. Redeclaration of the variable
-	Redecration of variable of only var is possible but not let, const.	

4. Reassignment
-	Reassignment is only possible for var and let but not for const

*/
```

<br/>
<hr/>
<br/>

### Question 10:

```javascript
// Question 10: What is destructuring in Javascript?


/* Notes:

-	Destructuing is feature introduced in ES6.
-	Destructuring allows to extract values from objects, arrays and assign them into some variables
- Destructuring is of 2 types, Objects and arrays
-	We can rename the values with colon : 
- We can get other properties using spread operator.
- We can skip the value by simply giving comma ,

Object Destructuring:
-	new variable name
-	Assigning the rest values

Array Destructuring:
-	skip values
-	Assigning the rest values
-	swap variables

*/

//Object Destructuring:

const obj = {
	name: "Sarfaraz",
	age: 37,
	designation: "frontend developer"
}

console.log(obj.name);
console.log(obj['name']);

/* let {name, age:myAge, designation} = obj;
console.log(name);
console.log(myAge);
console.log(designation); */

let {name, ...spreadOtherDetails} = obj
console.log(name);
console.log(spreadOtherDetails);

//-------- Destructuring array
const arr = [1,2,3,4,5]
const [one, ,three, ...spreadOther] = arr;

console.log(one);
console.log(three);
console.log(spreadOther);


//swap values
let a=10;
let b=20;
let temp;

//normal way to swap variables
/* temp = a;
a=b;
b=temp; */

[b,a] = [a,b]

console.log(a);
console.log(b);
console.log(temp);
```

<br/>
<hr/>
<br/>

### Question 11:

```javascript
//Question 11: Shallow Copy & Deep Copy in Javascript

/* Notes:
-	2 ways to copy object, shallow & Deep copy
-	Shallow Copy: Used to copy object
-	Deep copy: Copy nested objects
- We can not assign one object to another object, so above 2 concept come into picture.
-	Shallow copy: Object.assign is used.
-	We cant do deep copy using spread operato or Object.assign, as it will modify both the object
-	For Deep copy we need to convert it string using JSON.stringify --> then convert back to object using JSON.parse


*/

const obj = {
	name: "Sarfaraz"
}

//Shallow copy has 2 approaches
//Approach 1
// let copyObj = Object.assign({},obj);

//Approach 2: using spread operator 
let copyObj = {...obj}

copyObj.name = "Hussain"

console.log("Original Object:",obj);
console.log("Copy Object:", copyObj);


// console.log(`Original Object: ${obj}`); //it wont work, as we need to convert object into string using JSON.stringify

//Different ways to write object
/* console.log(`Original Object: ${JSON.stringify(obj)}`);
console.log("Original Object:", JSON.stringify(obj));
console.log("Original Object:",obj); */


//---------------- Example for nested object for Deep copy
const obj1 = {
	name: "Sarfaraz",
	address:{
		locality: "hitech city",
		city: "Hyderabad"
	}
}

// let copyObj1 = Object.assign({}, obj1); //not possible deep copy for nested object
let copyObj1 = JSON.parse(JSON.stringify(obj1)); //This is Deep copy


copyObj1.address.locality = "Gachibowli"
console.log("obj1:", obj1);
console.log("copyObj1:", copyObj1);

```

<br/>
<hr/>
<br/>

### Question 12:

```javascript
//Question 12: How to Create count of types in array

// Given an array show me the output

/* 
//Working example of reduce method

let num = [1,2,3,4,5]

//aproach 1
let result1 = num.reduce((accumulator, currVal)=>{
	return accumulator + currVal;
})
console.log(result1);

//aproach 2
let result2 = num.reduce((accumulator, currVal)=> accumulator + currVal)
console.log(result2); 

*/


let arr = [function(){}, new Object(), [], {}, NaN, Infinity, undefined, null, 0];

let result = arr.reduce((accumulator, currentVal)=>{
	let type = typeof currentVal;
	accumulator[type] = (accumulator[type] || 0) + 1
	return accumulator;

},{}) //here in reduce {} empty object means, gives the output in object.

console.log(result);
```

<br/>
<hr/>
<br/>

### Question 13:

```javascript
//Question 13: How to cut array length in Javascript

const arr = [1,2,3,4,5,6];

//Approach 12
// arr.length = 4;

//Approach 2:
arr.splice(2)
console.log(arr);
```

<br/>
<hr/>
<br/>

### Question 14:

```javascript
// Question 14: call(), apply(), bind()



const person1 = {
	name: "Sarfaraz",
	myFun(country){
		console.log(`My Name is ${this.name} and country is ${country}`);
	}
}

person1.myFun('India');


const person2 = {
	name: "Kamran",
	/* myFun(country){
		console.log(`My name is ${this.name} and country is ${country}`);
	} */
}

// person2.myFun('India');
person1.myFun.call(person2,'India');
person1.myFun.apply(person2,['Turkey']);
let bindFunc = person1.myFun.bind(person2,'India')
console.log(bindFunc());


/* Notes:
-	We can access key or value inside object using 'this' keyword
-	To avoid the duplicate code, we use call() method in javascript
-	In the above example, 2 object has repeated myFun, so we need to avoid this.
-	person1.myFun.call(person2,'India') : here we pass the object who want this function myFun
-	apply() is almost same to call() but only difference is passing parameter in array instead of string.
-	Whenever we want to reuse one function from one object to another then we use call() or apply() methods.
- bind() return new function, we pass the same type of string parameter as we did in call()

*/
```

<br/>
<hr/>
<br/>

### Question 15:

```javascript
//Question 15: Reverse a string

/*Notes:
-	input: Bye, ouput: eyb
- easy approach: str.split("").reverse().join("");
-	If we do using loop --> than Run the loop in reverse 
-	take 1 by 1 value in new string value
*/


let str = "Bye"
let newStr = "";

function reverse(str){
	for(let i=str.length-1; i >= 0; i--){
		newStr = newStr + str[i]
	}
	return newStr;
}

console.log(reverse(str));
```

<br/>
<hr/>
<br/>

### Question 16:

```javascript
//Question 16: Console log ordering

console.log('1');

setTimeout(()=> console.log('2'), 1000)

setTimeout(()=>{console.log('3')}, 2000)

setTimeout(()=>{console.log('4')},0);

console.log('5');


/* Notes:
setTimeout is blocking code, so it will call at the end based on time mentioned.
*/

/*
my guess:
1
5
4
2
3
*/
```

<br/>
<hr/>
<br/>

### Question 17:

```javascript
//Question 17: Strict mode 

/* Notes:

use strict:
- use strict directive is new in ECMAScript version 5
-	It means the code should execute in strict mode.
- 1. Variable must be declared before use.
-	2. Deleting a variable or function is not allowed.
-	3. Assigning a value to an undeclared variable is not allowed.

*/


//1.

//here variable is not declared, it is correct as it supports hoisting but not allowed in use strict mode.
// x = 10;
// console.log(x);

/* "use strict"
// x = 10;// not allowed using use strict
var x = 10;
console.log(x); */


//2.

/* "use strict"
function sum(a, b){
		return a + b;
}

delete sum; //not allowed to delete using strict mode */

/* "use strict"
var x = 10;
delete x; //not allowed to delete using strict mode */


//3.
"use strict"
function sum(a,b){
	result = a + b; //not allowed to use result without declaring it using strict mode
	return result;
}

console.log(sum(5, 10));



```

<br/>
<hr/>
<br/>

### Question 18:

```javascript
//Question 18: null vs undefined

/*

-	undefined means a variable has not been assigned.
-	null means an empty value, Means null value is defined by has empty value

- null and undefined are assignment values
-	compare with == gives true because both values are empty and === gives false because undefined type is undefined and null type is object
-	type of null is object and type of undefined is undefined
-	performing arithematic operations (0/NaN)


*/

// let a; // a is undefined
let a = null;
console.log(a);

//compare
console.log(undefined == null);
console.log(undefined === null);

console.log(typeof undefined);
console.log(typeof null);

let x = 20;
let y;
console.log(x*y);//output is NaN: as y is not defined- so it is NaN, 20*NaN = NaN

let xx = 10;
let yy = null;

console.log(xx * yy);//output: 0, here null means 0, so 10*0 = 0

```

<br/>
<hr/>
<br/>

### Question 19:

```javascript
// Question 19: map vs forEach

/* Notes:
-	map will convert array into loop
-	map return some value, benefit is we can use it any where. 
-	forEach doesn't return any value
-	map and forEach both are array's method to loop the array

*/

let arr = [1,2,3,4,5,6];

let mapArr = arr.map((val)=>{
	return val;
})

console.log(mapArr);


arr.forEach((val)=>{
	console.log(val);
})

/* //forEch deosnt return any value
let forEachArr = arr.forEach((val)=>{
	return val;
})

console.log(forEachArr); */
```

<br/>
<hr/>
<br/>

### Question 20:

```javascript
//Question 20: Hoisting

/* Notes:

-	A variable can used before it is declared.
	console.log(a);
	var a;
-	Hoisting applies to both variables and functions, but it works differently for each of them.
-	Hoisting will not work for {} curly bracket
-	Hoisting will not work for arrow function & variable function
- Hoisting only works for var but not for let, const
- Hoisting is not possible for function expression / arrow function, as in function expression / arrow function, value is stored in variable and variable dont know what it is.


*/

//variable hoisting
x = 10;
console.log(x);
var x;
// let x; //not possible

//function hoisting: function can be called first before function defination.
//Example:1
sum(10, 20);

function sum(a,b){
	console.log(a+b);
}

//Example: 2: 
// sum1(10, 20) //Not possible to call here, so hoiditing is not possible here.
{
	function sum1(a,b){
		console.log(a+b);
	}
}

sum1(10, 20) 


//Example 3:
//sum2(10,20); //Hoisting not posssible for function expression

var sum2 = function(a,b){
	console.log(a+b);
}

sum2(10,20); 

//Example 4: Hoisting with arrow function

//sum4(10, 20);  //Hoisting not posssible for arrow function

const sum4 = (a,b)=>{
	console.log(a+b);
}

sum4(10, 20);

```

<br/>
<hr/>
<br/>

### Question 21:

```javascript
//Question 21: What is Closures

/* Notes:

-	Closure means, an inner function has the access to the variables and parameters of its outer function.
-	Closure is similar to lexical scope.

*/

//Example 1:
const parent = (num2)=>{
	let num1 = 10;
	const child = ()=>{
		console.log(num1 + num2);
	}
	child();
}

parent(20);

//Example 2:
const parent1 = (num2)=>{
	let num1 = 10;
	const child =()=>{
		console.log(num1+num2);
	}
	return child; //Difference here
}

let parent1Result = parent1(5);
parent1Result();
```

<br/>
<hr/>
<br/>

### Question 22:

```javascript
//Question 22: Data types

/* Notes:

- How the browser will detect the type of data, so javascript has given different data type.
-	Javascript has main 2 data types
1. Primitive
2. Reference

1. Primitive:
-	String: Represents sequence of character, Example: "Hello word"
-	Number: Represents numerical value, Example: 2, 3.14
-	Boolean: Represents logical value, Which can be true or false.
-	Null: Represents the intentionally absence of any object value.
-	undefined: Represents the value that is not defined.
- BigInt, Symbol

2. Reference:
-	Object: Represents collection of properties & values
-	Array: Represents collection of elements

*/

// var x = 'sarfaraz';
// var x = 25;
// var x = true; 
// var x = null; //empty value
// var x;
// var x = {
// 	name: "Sarfaraz",
// 	age:37,
// 	position: "Frontend Developer"
// };

// var x = [1,2,3]
var x = ["Mango", "Banana"]

console.log(typeof x);


```

<br/>
<hr/>
<br/>

### Question 23:

```javascript
//Question 23: Array vs Object

/* Notes:

-	In Javascript, both array and object are used to store the collection of data, with some difference below,

-	Structure: 
	-	Array: Array is an ordered collection of data.
	-	Object: Object is an unordered collection of data.

-	Accessing Element: 
	-	Array: In Array, elements can be accessed using their numeric index.
	-	Object: In Object, elements can be accessed using their key, starting from 0.

-	Size: 
	-	Array: Arrays has a length property that tells you the number of elements in the array.
	-	Object: Objects do not have length property, but you can use Object.keys() method to get an array of the keys in the object
	and use the length property on that array to get the number of keys.

-	Type: 
	-	Arrays are a specific type of object in javascript. isArray() method is used to check the given array is array or not.
	- Example: console.log(Array.isArray([1,2,3])) --> output: true

*/

//Accessing elements in Arrays , Objects

//Instead of storing the values in many variables, we can store the multiple values in array
// let arr = [1,2,3,4,5];
let arr = ["mango", "banana", "apple"]
console.log(arr[2]);

//We can keep all information at one place in key value pair
let obj = {
	name: "Sarfaraz",
	age: 37,
	designation: "Frontend developer"
}

console.log(obj);
console.log(obj.name);
console.log(obj['name']);

//size
let arr1 = [1,2]
console.log(arr1.length);

let obj1 = {
	name: "kamran",
	age: 32,
	designation: "DevOps Engineer"
}

console.log(Object.keys(obj1));
console.log(Object.values(obj1));


//Type
let arr2 = [1,2];
console.log(Array.isArray(arr2));

let arr3 = [];
console.log(Array.isArray('arr3')); //intentionally given in strings

let arr4 = new Array(5);
console.log(Array.isArray(arr4));

let arr5 = new Int16Array([15,33]);// we cant define array like 'Int16Array' but with Array
console.log(Array.isArray(arr5));
```

<br/>
<hr/>
<br/>

### Question 24:

```javascript
//Question 24: Cllback

/* Notes: 
-	A callback function is a function passed into another function as an argument.
-	A callback function can run after another function has finished.

*/

const firstFun = (name, secondFun)=>{
		console.log(`My Name is ${name}`);
		secondFun();
}

const secondFun = ()=>{
	console.log(`This is callback function`);
}

firstFun("Sarfaraz", secondFun);// Here secondFun is a callback function, passed as an argument to another function.
// secondFun();
```

<br/>
<hr/>
<br/>

### Question 25:

```javascript
//Question 25: Callback hell

/* Notes: 

-	Callback hell is a situation that arises in javascript programming when you have mulitple nested callbacks.
-	Callback hell look like a pyramid.
-	Callback hell can be avoided using promises, async-await.

*/


//Scenario: after every 2 sec, start new task
setTimeout(()=>{
	console.log('First task started');
	setTimeout(()=>{
		console.log('Second task started');
		setTimeout(()=>{
			console.log('Third task started');
			setTimeout(()=>{
				console.log('Fourth task started');
				setTimeout(()=>{
					console.log('Fifth task started');
				},2000)
			}, 2000)
		},2000)
	}, 2000)
}, 2000);

//The above scenario is called callback hell, as we are running callback one after another.


```

<br/>
<hr/>
<br/>

### Question 26:

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>
<body>
	
</body>
<script>
	//Question 26: Normal vs Arrow function

/* Notes: 

-	In function declaration hoisting is possible, but with function expression hoisting is not possible.
-	Arguments wont work with arrow function, if we want to make argument work then we can use destructuring 
-	no prototypes for arrow function, as we dont have constructor function for arrow function.
-	new keyword not working with arrow function: Arrow function doesnt have new keyword
-	arrow function dont have 'this' keyword: Arrow function doesnt have this keyword

*/


//--------------- Explaination: Function Declaration & Function Expression

myFun1(10,20);
// myFun2(10, 20); // function expression cant be hoisted.

//Function Declaration 
function myFun1(a,b){
	console.log(a+b);
	return a + b;
}

// Function Expression
let myFun2 = function(a,b){
	console.log(a+b);
	return a + b;
}

// myFun1(10,20);
// myFun2(10, 20);

//--------- other way to write myFun2, or function expression using arrow function
const arrow1 = (a,b)=>{
	console.log(a+b);
	return a+b;
}

arrow1(5, 10);

//Arrow function in 1 line
const arrow2 = (a,b)=> a+b;
console.log(arrow2(5,10));

//---------------- function with Agruments

function normal(a,b){
	console.log(arguments);
	return a+b;
}
normal(10, 20, 30, 40);

// const arrow3 = (a,b) => console.log(arguments); //not possible to access arguments directly
const arrow3 = (...values) => console.log(values); //not possible to access arguments directly
arrow3(10, 20, 30, 40);


//--------------- No prototype for arrow function
function normal1(a,b){
	return a+b;
}

const arrow4 = (a,b)=>{
	return a+b;
}

//
// normal1(10, 20);
// arrow4(10,20,30,40);
console.log("No prototype for arrow function");
console.log(normal1.prototype);
console.log(arrow4.prototype);


//----------------- new keyword
console.log(new normal1());
// console.log(new arrow4());//not possible with arrow function

//------ arrow function with this keyword 
const obj = {
	name: "sarfaraz",
	normal: function(){
		console.log(`my name is ${this.name}`);
	},
	arrow: () => {
		console.log(`My name is ${this.name}`);//cant work as this wont work in arrow function.
	}
}

console.log(obj.normal());
console.log(obj.arrow());

</script>
</html>
```

<br/>
<hr/>
<br/>

### Question 27:

```html

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
	<style>
		body{
			display: flex;
			align-items: center;
			justify-content: center;
			height: 100vh;
		}
		#parentClick{
			width: 200px;
			height: 200px;
			background: indianred;
			display: flex;
			align-items: center;
			justify-content: center;
		}
	</style>
</head>
<body>
	<div id="parentClick">
		<button id="childClick">Click</button>
	</div>
</body>
<script>
	//Question 27: Event Bubbling

/* Notes:

-	Event Bubbling: It is a behaviour in javascript, where events trigged on a nested element will "bubble up"
and trigger events on all of its parent elements.
-	To stop the event bubbling, you can use stopPropagation() method.
- Example: when we click child then it parent is also called.

*/

const parentId = document.getElementById("parentClick");
const childId = document.getElementById("childClick");


const parentClick = ()=>{
	alert("parent called");
}

const childClick = ()=>{
	alert("child called");
	event.stopPropagation();
}

parentId.addEventListener('click',parentClick, false);
childId.addEventListener('click', childClick, false);




</script>
</html>




```

<br/>
<hr/>
<br/>

### Question 28:

```html

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
	<style>
		body{
			display: flex;
			align-items: center;
			justify-content: center;
			height: 100vh;
		}
		#parentClick{
			width: 200px;
			height: 200px;
			background: indianred;
			display: flex;
			align-items: center;
			justify-content: center;
		}
	</style>
</head>
<body>
	<div id="parentClick">
		<button id="childClick">Click</button>
	</div>
</body>
<script>
	//Question 27: Event Capturing

/* Notes:

-	Event Capturing: It is a behaviour in javascript, here parent event should call first then child event.
-	To stop the event Capturing, you can use true in addEventListener for both parent and child.

*/

const parentId = document.getElementById("parentClick");
const childId = document.getElementById("childClick");


const parentClick = ()=>{
	alert("parent called");
}

const childClick = ()=>{
	alert("child called");
}

parentId.addEventListener('click',parentClick, true);
childId.addEventListener('click', childClick, true);




</script>
</html>




```

<br/>
<hr/>
<br/>

### Question 29:

```javascript
//Question 29: sort() method

/* Notes:

-	sort() is an array method, used for sorting an array
-	for number it is not sorting properly, so we pass 2 parameters a, b
	- for ascending sort, sort((a,b)=> a-b)
	- for descending sort, sort((a,b)=> b-a)	

*/

const stringArr = ["banana", "mango", "apple"]
console.log(stringArr.sort());

const numArr = [5,44,8,31,2]
console.log(numArr.sort((a,b)=> a-b));

```

<br/>
<hr/>
<br/>

### Question 30:

```javascript
//Question 30: How to add Object within array

let a = [
	{
		a:1,
		b:2,
		c:3,
	}
];

let d = { d: 4}

/* output: 
[
	{
		a:1,
		b:2,
		c:3,
		d:4
	}
] 

*/

// let result = Object.assign({}, a, d)
//our intention to add d in a at '0' location

//Approach 1:
// a[0]['d'] = 4

//Approach 2:
a[0] = {...a[0], ...d}
console.log(a);
```

<br/>
<hr/>
<br/>

### Question 31:

```javascript
//Question 31: How to merge object and array in javascript

/* Notes:

merge objects:

merge arrays using:
-	array.concat() & [].concat()
-	arra.push()
-	destructuring

*/

//inputs
const carOne = {
	color: 'blue',
	status: { running:true, passenger: 4, wiperlfuid: "empty", name:"sarfaraz"},
	age: 5,
	miles: 50000,
	value: '8000'
}

const carTwo = {
	color: "green",
	status: { running: 'yes', passenger:2, fuelTank: "empty"},
	value: 9000
}

//Scenario: how to merge the objects
//Here, when key is same, then keep the second value of an object, means override the second value

const result = {...carOne, ...carTwo}
console.log(result);



//------------------- array merge

const arr1 = [1,2,3,4,5];
const arr2 = [6,7,8,9,10];
const arr3 = [11,12,13,14,15,15];

//--> using concat()
// const resultArr = arr1.concat(arr2, arr3);
const resultArr = [].concat(arr1, arr2, arr3);
console.log(resultArr);

//--> using push
// arr1.push('test');
arr1.push(...arr2, ...arr3);//it will spread the values of array using spread operator.
console.log(arr1);

//easy way
let resultArr2 = [...arr2, ...arr3];
console.log(resultArr2);

```

<br/>
<hr/>
<br/>

### Question 32:

```javascript
//Question 32: Find unique values in an array

/* Notes: 
There are 3 ways using below,
-	filter() & indexOf()
-	reduce()
-	set Object

*/

// using filter & indexOf
const arr = [1,1,2,3,3,4,5,6,6];
const uniqueValues = arr.filter((value, index, self)=>{
	return self.indexOf(value) == index;
})

console.log(uniqueValues);


//using reduce
const arr1 = [1,1,2,3,3,4,5,6,6];
const uniqueValues1 = arr1.reduce((accumulator, currentVal)=>{
	//check if the value is not include in current value
	if(!accumulator.includes(currentVal)){
		accumulator.push(currentVal);
	}
	return accumulator;
},[])

console.log(uniqueValues1);


//using set
const arr2 = [1,1,2,3,3,4,5,6,6];
const result2 = [...new Set(arr2)];
console.log(result2);
```

<br/>
<hr/>
<br/>

### Question 33:

```javascript
//Question 33: Anonymous function


/* Notes:
- Anonymus function mostly used, when we dont want to store the name of function in memory
- Anonymus function used when we dont want to call it multiple times. or no needed to reuse.

*/

//mostly we use the function with function name
function one(){
	console.log('this is normal function');
}

one();

//example: 2
var withoutNameFun = function(){
	console.log('this is anonymous function which has no name');
}

console.log(withoutNameFun());


//Example3: setTimtout is using anonymous function
setTimeout(()=>{
	console.log('this is settimeout function console');
},2000)
```

<br/>
<hr/>
<br/>

### Question 34:

```javascript
//Question 34: First class function

/* Notes: 

First class function:
-	1. Assigning a function to a variable
-	2. Passing a function as an argument
-	3. Returning a function

*/


// 1. Assigning a function to a variable
var myFun = function(){
	console.log('this is funtion with no name');
}

myFun();


// 2. Passing a function as an argument
function myFun1(){
	return 'This is a function';
}

function main(yourFun, name){
	console.log(yourFun(), name);
}
main(myFun1, "sarfaraz");

// 3. Returning a function to another function
function a(){
	return function b(){
		console.log('this is a function b');
	}
}
a()(); //()() this means, we want to call inner function using outer function.

//or instead of a()()
var x = a();
x();
```

<br/>
<hr/>
<br/>

### Question 35:

```javascript
//Question 35: comma operator 


/* Notes:

-	The comma , operator evaluates each of its operands (from left to right) and return the value of the last operand.

*/

let x = 1;

x = (x++, x)
console.log(x);

x = (2,3);
console.log(x);

let xx = (3+6, 7+2);
console.log(xx);

let yy = (3,6) + (7,2);
console.log(yy);

let zz = (a=10, b=20, a+b);
console.log(zz);


```

<br/>
<hr/>
<br/>

### Question 36:

```javascript
//Question 36: Ternary Operator

/* Notes:

- Shorter syntax of if else condition


*/

let x = 11;
if(x == 10){
	console.log('yes');
}else{
	console.log('No');
}

//using ternary oprator
const result = x == 10 ? 'yes': 'No';
console.log(result);
```

<br/>
<hr/>
<br/>

### Question 37:

```javascript
//Question 37: Find duplicate in array

let arr= [1,2,2,3,4,4,5,7,7,1]

let duplicate = arr.filter((value, index, self)=>{
	return self.indexOf(value) !== index
});

console.log(duplicate);
```

<br/>
<hr/>
<br/>

### Question 38:

```javascript

//Question 38: Find and findIndex

const arr = [10, 22, 20, 30, 40, 50]

//Scenario: check value above 20
//find(): check till 20 find, then it will skip checking further. and print that finded value. in filter, it will return all remaining values
//findIndex(): It will check based on the index and return the index.


const result1 = arr.find(function(val){
	return val > 20;
})
console.log(result1);//22

//---------------- or

const result2 = (val) =>  val > 20; 
console.log(arr.find(result2));//22


//----- Example using findIndex
const result3 = arr.findIndex(function(val){
	return val > 20;
})

console.log(result3);

```

<br/>
<hr/>
<br/>

### Question 39:

```javascript

//Question 39: some()

/* Notes: 

some()
-	if condition match in some(), then it will return true or false
-	some() will check all values 1 by 1

*/

const arr = [5, 10, 15, 20, 25]

//check vak greater than 18
const checkAge = (val)=>{
		return val >= 18
}
const result = arr.some(checkAge);
console.log(result); //true

//Example 2

const person = [
	{
		name: "KL Rahul",
		age: 30
	},
	{
		name: "Ishan",
		age: 25
	},
	{
		name: "Jaiswal",
		age: 20
	}
]

//check age is greater then 24
const ageCheck = (val)=>{
	return val.age >=24;
}

const result2 = person.some(ageCheck);
console.log(result2);
```

<br/>
<hr/>
<br/>

