## For more array methods follow this link 
follow this link for more array methods in details
```
https://www.programiz.com/java-programming/library/arraylist
https://www.programiz.com/javascript/library/array
```


## JavaScript Array concat()
(returns new array )

The concat() method returns a new array by merging two or more values/arrays.

```
let primeNumbers = [2, 3, 5, 7]
let evenNumbers = [2, 4, 6, 8]

join two arrays 
let joinedArrays = primeNumbers.concat(evenNumbers);
console.log(joinedArrays);

Output:
[
  2, 3, 5, 7,
  2, 4, 6, 8 


  
]
```

Run Code
concat() Syntax
The syntax of the concat() method is:
```
arr.concat(value1, value2, ..., valueN)
```

concatenating a value and array
```
var new_arr1 = languages2.concat("Lua", languages1);
console.log(new_arr1); // [ 'C', 'C++', 'Lua', 'JavaScript', 'Python', 'Java' ]
```

## Javascript Array filter()
The filter() method returns a new array with all elements that pass the test defined by the given function.

```
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// function to check even numbers
function checkEven(number) {
  if (number % 2 == 0)
    return true;
  else
    return false;
}

// create a new array by filter even numbers from the numbers array
let evenNumbers = numbers.filter(checkEven);
console.log(evenNumbers);

// Output: [ 2, 4, 6, 8, 10 ]
```

## JavaScript Array find()
The find() method returns the value of the first array element that satisfies the provided test function.

```
let numbers = [1, 3, 4, 9, 8];

function to check even number
function isEven(element) {
  return element % 2 == 0;
}

get the first even number
let evenNumber = numbers.find(isEven);
console.log(evenNumber);

 Output: 4
```

arrow function 
```
function isEven(element) {
  return element % 2 == 0;
}

let randomArray = [1, 45, 8, 98, 7];

let firstEven = randomArray.find(isEven);
console.log(firstEven); // 8

// using arrow operator
let firstOdd = randomArray.find((element) => element % 2 == 1);
console.log(firstOdd); // 1
```

find returns the complete object with elements 

```
const team = [
  { name: "Bill", age: 10 },
  { name: "Linus", age: 15 },
  { name: "Alan", age: 20 },
  { name: "Steve", age: 34 },
];

function isAdult(member) {
  return member.age >= 18;
}

console.log(team.find(isAdult)); // { name: 'Alan', age: 20 }

// using arrow function and deconstructing
let adultMember = team.find(({ age }) => age >= 18);

console.log(adultMember); // { name: 'Alan', age: 20 }
```
## JavaScript Array findIndex()

The findIndex() method returns the index of the first array element that satisfies the provided test function or else returns -1.

```
// function that returns odd number
function isOdd(element) {
  return element % 2 !== 0;
}

// defining an array of integers
let numbers = [2, 8, 1, 3, 4];

// returns the index of the first odd number in the array
let firstOdd = numbers.findIndex(isOdd);

console.log(firstOdd);

// Output: 2
```

eg2 
```
// function that returns even number
function isEven(element) {
  return element % 2 == 0;
}

// defining an array of integers
let numbers = [1, 45, 8, 98, 7];

// returns the index of the first even number in the array
let firstEven = numbers.findIndex(isEven);

console.log(firstEven); // 2
```

arrow function 
```
// defining an array
let days = ["Sunday", "Wednesday", "Tuesday", "Friday"];

// returns the first index of 'Wednesday' in the array
let index = days.findIndex((day) => day === "Wednesday");

console.log(index); // 1
```

## Javascript Array forEach()

```
let numbers = [1, 3, 4, 9, 8];

// function to compute square of each number
function computeSquare(element) {
  console.log(element * element);
}

// compute square root of each element
numbers.forEach(computeSquare);

/* Output:
1
9 
16
81
64
*/
```

arrow function 

```
const numbers = [1, 2, 3, 4, 5];

// Using arrow function in forEach
numbers.forEach((num, index) => {
  console.log(`Element at index ${index} is ${num}`);
});

output 

Element at index 0 is 1
Element at index 1 is 2
Element at index 2 is 3
Element at index 3 is 4
Element at index 4 is 5
```

## Javascript Array.from()

The from() method creates a new array from any array-like or iterable object.
```
// creating a new array from string
let newArray = Array.from("abc");

console.log(newArray);

// Output:
// [ 'a', 'b', 'c' ]
```

## JavaScript Array includes()
The includes() method checks if an array contains a specified element or not.

```
// defining an array
let languages = ["JavaScript", "Java", "C"];

// checking whether the array contains 'Java'
let check = languages.includes("Java");

console.log(check); 

// Output: true
```
## JavaScript Array indexOf() 

The indexOf() method returns the first index of occurance of an array element, or -1 if it is not found.

```
let languages = ["Java", "JavaScript", "Python", "JavaScript"];

// get the index of the first occurrence of "JavaScript"
let index = languages.indexOf("JavaScript");
console.log(index);

// Output: 1
```

## JavaScript Array lastIndexOf()
The lastIndexOf() method returns the index of the last occurrence of a specified element in the array.

```
let priceList = [10, 8, 2, 31, 10, 31, 65];

// finding the index of the last occurence of 31
let lastIndex = priceList.lastIndexOf(31);

console.log(lastIndex); 

// Output: 5
```

```
let alphabets = ["a", "b", "c", "a", "d"];

// finding the index of the last occurence of 'a'
let lastIndex1 = alphabets.lastIndexOf("a");

console.log(lastIndex1);

// finding the index of the last occurence of 'e'
let lastIndex2 = alphabets.lastIndexOf("e");

console.log(lastIndex2);
```
## JavaScript Array map()
The map() method creates a new array with the results of calling a function for every array element.

```
let numbers = [2, 4, 6, 8, 10];

// function to return the square of a number
function square(number) {
  return number * number;
}

// apply square() function to each item of the numbers list
let square_numbers = numbers.map(square);
console.log(square_numbers);

// Output: [ 4, 16, 36, 64, 100 ]

```
 arraow function 

```
// custom arrow function
const string = "JavaScript";
const stringArr = string.split(''); // array with individual string character

let asciiArr = stringArr.map(x => x.charCodeAt(0));
```
## JavaScript Array slice()
(returns array )
The slice() method returns a shallow copy of a portion of an array into a new array object.

```
let numbers = [2, 3, 5, 7, 11, 13, 17];

// create another array by slicing numbers from index 3 to 5
let newArray = numbers.slice(3, 6);
console.log(newArray);

// Output: [ 7, 11, 13 ]
```

```
let languages = ["JavaScript", "Python", "C", "C++", "Java"];

// slicing the array (from start to end)
let new_arr = languages.slice();
console.log(new_arr); // [ 'JavaScript', 'Python', 'C', 'C++', 'Java' ]

// slicing from the third element
let new_arr1 = languages.slice(2);
console.log(new_arr1); // [ 'C', 'C++', 'Java' ]

// slicing from the second element to fourth element
let new_arr2 = languages.slice(1, 4);
console.log(new_arr2); // [ 'Python', 'C', 'C++' ]
```

## Javascript Array some()
(returns boolen)

```
// a test function: returns an even number
function isEven(element) {
  return element % 2 === 0;
}

// defining an array
let numbers = [1, 3, 2, 5, 4];

// checks whether the numbers array contain at least one even number
console.log(numbers.some(isEven));

// Output: true 
```

## JavaScript Array splice()
(returns array)

The splice() method modifies an array (adds, removes or replaces elements).

```
let prime_numbers = [2, 3, 5, 7, 9, 11];

// replace 1 element from index 4 by 13
let removedElement = prime_numbers.splice(4, 1, 13);
console.log(removedElement);
console.log(prime_numbers);

// Output: [ 9 ]
//         [ 2, 3, 5, 7, 13, 11 ]

```





