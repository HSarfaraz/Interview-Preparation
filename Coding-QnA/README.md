## Javascript Output questions

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

