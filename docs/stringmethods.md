## LENGTH METHOD 
(returns string)
 These methods return a new string with little change from the original string.
 	The length is a string property that is used to find the length of a string. 
    It returns the number of characters in the string including spaces.
	Read-only means that the strings created in JavaScript are immutable
	The length property returns the number of characters in a string.

    
	var str = "Hello World";
      str.length; // 11
      

## Charat()
(returns string)
The charAt() string method in javascript returns a character at the specific index of the given string. The charAt() method takes the index value as an argument and returns the corresponding character from the calling string.
         An index value of a string starts with 0, which means the first character has an index value of 0, the second character has an index value of 1, and so on


```
eg-1 // string declaration
        const string = "Hello World!";

        // finding character at index 1              
          let  index1 = string.charAt(1);

      console.log("Character at index 1 is " + index1);

      // Output: 
      // Character at index 1 is e

 eg-2
const str = "Hello World";
//default index value = 0, return first character
console.log(str.charAt());
// index out of range, return empty string
console.log(str.charAt(13));
// index can't be converted to an integer, return first character
console.log(str.charAt('a'));


  eg-3 
  let sentence = "Happy Birthday to you!";

// finding character at index 100 
let result = sentence.charAt(100);

console.log("Character at index 100 is: " + result);

returns the empty string 

```
## charCodeAt 
(returns number)
The charCodeAt string method in javascript returns the Unicode value (between 0 and 65535) of the character present at the given index of the string. Example Unicode value of 'A' is 65.
The charCodeAt() method takes an index as an argument and returns the Unicode value of the character present at that index value.

```
EG-1
// string definition
const greeting = "Good morning!";

// UTF-16 code unit of character at index 5
let result = greeting .charCodeAt(5);

console.log(result);

// Output: 109

eg-2 
console.log(str.charCodeAt("x"));
// Out of range returns NaN
```

## concat 
(return new string)

The concat string method in javascript concatenates the passed string in the method to the calling string and returns the concatenated string as a new string.

new string = str1+ str2 

 Note: for concatenation of string it is suggested to use assignment operators (+ or +=) instead of the concat method.

## endsWith

 returns boolen (true or false ) 

 The endsWith string method in javascript is used to determines whether the string ends with a specified substring or not.
If it ends with a specified string then it returns true, else returns false.

```
eg-1 
const question = "What is DOM?";
// using endsWith method
// checks whether the string ends with "?"
console.log(question.endsWith("?"))
```

we can pass the 2 arguments 
There is also a second argument in the method which is optional. It specifies a length value for the string. If you pass the length value is 5 then it will see only the first 5 characters of the string.
Please note that endsWith() method is case sensitive.

```
Example
const question = "What is DOM?";
// check only first 5 characters
console.log(question.endsWith("?", 5));
```

## String includes
(returns boolen )
The includes string method in javascript is used determines whether a given substring is present in the calling string or not.
If the string is present then the method returns true, if not substring is not present then the method returns false.
The matching of includes() method for the string is case-sensitive.
selectedRelation = (['Mother', 'Father','Spouse'].includes(selectRelationToPatient) && !selectedRelation) ? selectRelationToPatient : selectedRelation;

```

Example

const sentence = "Carbon emission is increasing Day by day.";

check if the string contains words
console.log(sentence.includes("day")); // true
console.log(sentence.includes("Day")); // true
console.log(sentence.includes("DAY")); // false

```
we can pass 2 arguments in it we can search with the exact number or the position 
```
Example 2:
const sentence = "Carbon emission is increasing day by day.";

checking from the index 20
console.log(sentence.includes("is", 20));
checking from the index 2
console.log(sentence.includes("is", 2));
checking from the index 5
console.log(sentence.includes("emission", 5));
```
## indexOf 
(returns number)

The indexOf string method in javascript is used to get the index of the first occurrence of a specified value in a string.
If the character or substring is not present then it returns -1. The search string is case-sensitive.

2nd argument 
There is a second argument that is optional that defines the start index from where the method starts to search for the character or substring
```
Example
const sentence = "Carbon emission is increasing day by day";

// no substring provided to search        
console.log(sentence.indexOf());
console.log('undefined'.indexOf());
// start searching from index 40
console.log(sentence.indexOf("day", 40));
```
## String lastIndexOf
(returns number)

count the last vlaue 
var str = "I love Java  Java Java ok ok Java(takes the last value );

```
//  lastIndexOf() with "javaScript" as  substr
var result2 = str.lastIndexOf("Java");

```

The lastIndexOf() string method in javascript searches the last occurrence of a substring within a string. The method starts searching from the end of the string for efficiency.
If the substring is not in the given string then it returns -1.

## match
( returns in array )
The match() string method in javascript uses a regular expression to match a series of characters within the calling string.
The method returns the output as an array of string with matched character or strings as its element.
If the parameter passed is not a regular expression then it is implicitly converted to RegExp by using new RegExp(regexp).

```
Example
const series = "bdWg2AdjgH4du5jUgT";

// match all capital letters and numbers
console.log(series.match(/[A-Z0-9]/g));

```
If the used regular expression does not have a g flag then the method returns only the first complete match and its capturing group.
If nothing matches within the string then the method returns null.

```
Example

const string = "to do or not to do";

// no g flag
console.log(string.match(/do/));
// no match found, return null
console.log(string.match(/dog/));

```

## matchall
(returns string)
The matchAll() method in JavaScript is used with strings to return all matches of a regular expression in a string
```
Vconst text = "The quick brown fox jumps over the lazy dog. The dog was not amused.";
const regex = /dog/g; // Regular expression with global flag 'g' to find all matches

const matches = text.matchAll(regex); // Using matchAll() to find all matches
```
## repeat
(retuns string)

The repeat() method concatenates a passed string by a specified number of times and return it as a new string.

A number of times string is to be repeated is passed as an argument in the method, where the number lies between 0 and +Infinity.
If a decimal value is passed then it will be converted to an Integer when passed.
The method reports an error for a negative number.
```
Example
const str = "Tick tock, ";

// repeat the string by 2 times
console.log(str.repeat(2));
// converts the decimal value to integer
console.log(str.repeat(3.5));
// repeat 0 times
console.log(str.repeat(0));
```

## replace
(returns the new string )

```
const message = "bbb ccc";

// replace the first b with c
let result = message.replace('b', 'c');
console.log(result);

resut = "cbb ccc"  here we can see that only starting value is changed here 
```
## replaceAll() 
(returns the new string)
it is replace with every word or charector in it 
  
Note: While using regular expression in the replaceAll() method using a global flag (g) is compulsory with it otherwise it will throw a 'TypeError'
```
const str = "Carbon emission is increasing day by day.";

// select all match using both string or regular expression
console.log(str.replaceAll("day", "year"));
console.log(str.replaceAll(/day/g, "month"));

Carbon emission is increasing year by year.
Carbon emission is increasing month by month.
```
## search
(returns number)

returns the index of the match string 
search also work as same as the match 
String match() and String search() The match() method returns an array of matches.
The search() method returns the position of the first match.

```
const text = "The quick brown fox jumps over the lazy dog.";
const index = text.search("fox");

console.log(index); // Output: 16
```

## slice method
(returns new string)
The slice string method in javascript extracts a part of the string and returns it as a new string.

slice consist of 2 indexs or argumenst 

str.slice(startindx , lastindex )- print between those values 

```
const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus = fruits.slice(1, 3);

output - Orange,Lemon

```

## split 
(returns string)
The split string method in javascript divides the given string intro substring and returns an array of substrings.
```
const sentence = "Carbon emission is increasing day by day";

// no pattern -> return whole string in array
console.log(sentence.split());
// split at each space
console.log(sentence.split(''));
// split at each space
console.log(sentence.split(' '));
// split at each 'is'
console.log(sentence.split('is'));

console.log("ABCDEF".split("")); // [ 'A', 'B', 'C', 'D', 'E', 'F' ]

const text = "Java is awesome. Java is fun.";

let pattern = ".";
let newText = text.split(pattern);
console.log(newText); // [ 'Java is awesome', ' Java is fun', '' ]

let pattern1 = ".";
// only split string to maximum to parts
let newText1 = text.split(pattern1, 2);
console.log(newText1); // [ 'Java is awesome', ' Java is fun' ]

const text2 = "JavaScript ;  Python ;C;C++";
let pattern2 = ";";
let newText2 = text2.split(pattern2);
console.log(newText2); // [ 'JavaScript ', '  Python ', 'C', 'C++' ]

// using RegEx
let pattern3 = /\s*(?:;|$)\s*/;
let newText3 = text2.split(pattern3);
console.log(newText3); // [ 'JavaScript', 'Python', 'C', 'C++' ]
```
## startsWith
(returns boolean)
The startsWith string method in javascript determines whether a string starts with some given substring or not. If it starts with the desired string then it returns true else return false.

The search string is passed as the first argument to the method. There is also an optional argument that defines the position from where the method should start checking.
The startsWith method is case-sensitive.

```
Example:
const sentence = "Carbon emission is increasing day by day";
console.log(sentence.startsWith("Car"));
console.log(sentence.startsWith("carbon")); // return false case-sensitive
```
## substring 
(returns string)
The substring method in JavaScript is used to extract a part of a string between two indices or positions. It's a common method and can be used within any JavaScript code, including Angular components.
```
string.substring(startIndex, endIndex)
```
startIndex: The position where the extraction begins.
endIndex (optional): The position where the extraction ends (but does not include the character at this index). If omitted, the method will extract to the end of the string.

```
fullText: string = 'Hello, Angular!';
extractedText: string;
// Extract a substring starting from index 7 to the end
this.extractedText = this.fullText.substring(7);
// Output: 'Angular!'
    
// Extract a substring from index 7 to 13 (not including 13)
const partialText = this.fullText.substring(7, 13);
console.log(partialText); // Output: 'Angular'
```

differnce between substring and substr 

```
string.substring(startIndex, endIndex)
string.substr(startIndex, length)


```

```
let text = "JavaScript";

// Extracts 6 characters starting from index 4
console.log(text.substr(4, 6)); // Output: "Script"

// Extracts from the end of the string if negative index is provided
console.log(text.substr(-6, 6)); // Output: "Script"

// Extracts to the end if length is omitted
console.log(text.substr(4)); // Output: "Script"

```

```
substr

let text = "JavaScript";

// Extracts 6 characters starting from index 4
console.log(text.substr(4, 6)); // Output: "Script"

// Extracts from the end of the string if negative index is provided
console.log(text.substr(-6, 6)); // Output: "Script"

// Extracts to the end if length is omitted
console.log(text.substr(4)); // Output: "Script"

```

Use substring() if you need to work with two indices, or if you are concerned about browser compatibility and future-proofing your code.
Use substr() if you need to extract a specific number of characters from a certain position, but keep in mind that it is deprecated.

## To lowercase , To upper case
(returns the new string)

to covert it into lowe case 
to convert into upper case 

## toString 
(returns string)

convert it into the string 

## trim 
(returns string)
The trim() string method in javascript removes whitespaces from both ends of the string. Whitespaces are space, tabs, newline, etc.
```
Example
const str = "    TutorialsTonight    ";
console.log(str.trim());

oputput- TutorialsTonight
```
## valueOf

The valueOf() string method in javascript returns the primitive value of a String object.
```
Example
const str = new String("hello world");
console.log(str.valueOf(str))

output - Hello world without string 
```


toUpperCase()
trim()
trimEnd()
trimStart()
valueOf()
JS TypedArray

Window
Window Object
Window Console
Window History
Window Location
Window Navigator
Window Screen

HTML DOM
HTML Documents
HTML Elements
HTML Attributes
HTML Collection
HTML NodeList
HTML DOMTokenList
HTML Styles

HTML Events
HTML Events
HTML Event Objects
HTML Event Properties
HTML Event Methods

Web APIs
API Canvas
API Console
API Fetch
API Fullscreen
API Geolocation
API History
API MediaQueryList
API Storage
API Validation
API Web

HTML Objects
<a>
<abbr>
<address>
<area>
<article>
<aside>
<audio>
<b>
<base>
<bdo>
<blockquote>
<body>
<br>
<button>
<canvas>
<caption>
<cite>
<code>
<col>
<colgroup>
<datalist>
<dd>
<del>
<details>
<dfn>
<dialog>
<div>
<dl>
<dt>
<em>
<embed>
<fieldset>
<figcaption>
<figure>
<footer>
<form>
<head>
<header>
<h1> - <h6>
<hr>
<html>
<i>
<iframe>
<img>
<ins>
<input> button
<input> checkbox
<input> color
<input> date
<input> datetime
<input> datetime-local
<input> email
<input> file
<input> hidden
<input> image
<input> month
<input> number
<input> password
<input> radio
<input> range
<input> reset
<input> search
<input> submit
<input> text
<input> time
<input> url
<input> week
<kbd>
<label>
<legend>
<li>
<link>
<map>
<mark>
<menu>
<menuitem>
<meta>
<meter>
<nav>
<object>
<ol>
<optgroup>
<option>
<output>
<p>
<param>
<pre>
<progress>
<q>
<s>
<samp>
<script>
<section>
<select>
<small>
<source>
<span>
<strong>
<style>
<sub>
<summary>
<sup>
<table>
<tbody>
<td>
<tfoot>
<th>
<thead>
<tr>
<textarea>
<time>
<title>
<track>
<u>
<ul>
<var>
<video>

Other References
CSSStyleDeclaration
JS Conversion




JavaScript String valueOf()
Example
Get the value of a text:

let text = "Hello World!";
let result = text.valueOf();
The same as:

let text = "Hello World!";
let result = text;
More examples below.

Description
The valueOf() method returns the primitive value of a string.

The valueOf() method does not change the original string.

The valueOf() method can be used to convert a string object into a string.






