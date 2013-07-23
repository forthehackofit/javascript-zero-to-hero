# JS Foundations - P. I
* Variables
* Conditional Statements
* Loops



# Variables
1. Assigment
2. Data Types
3. by Value or by Reference
4. Type conversion
5. Scope


## Assignment

```javascript
var first = "Ady",
    last  = 'Ngom',
    luckyNumber = 9,
    ppg = 22.5,
    isHandsome = true,
    isNice,
    _private = null,
    hobbies = ["JS", "Basketball", "Baby talk"],
    meetups = { "js" : "JS Zero to Hero", "html" : "HTML5 & CSS3"};
```


## Data Types
```javascript
(typeof first); // "Ady" is a string
(typeof last); // 'Ngom' is a string
(typeof luckyNumber); // 9 is a number
(typeof ppg); // 22.5 is also a number
(typeof isHandsome); // true is a boolean
(typeof _private); // null is an object (weird)
(typeof isNice); // isNice has no value so it is undefined
(typeof hobbies) // hobbies is an object (array are objects in JS)
(typeof meetups) // an object with key : value pairs
```


## by Value or by Reference


### Scalar variables are passed by value

```javascript
var a = 1;
var b = a;
b = 5;
console.log(a); // 1
console.log(b); // 5

var slogan = "Home of the braves";
var motto = slogan;
console.log(motto); // Home of the braves
motto = "Land of the free";
console.log(slogan) // Home of the braves
console.log(motto) // Land of the free
```


### Dimensional variables are passed by reference

```javascript
var obj1 = { first : "John", last : "Doe", gender : "male" };
var obj2 = obj1;
obj2.first = "Jane";
obj2.gender = "female";
console.log(obj1); // { first : "Jane", last : "Doe", gender : "female" }

var fruits = ["banana", "orange", "apple"];
var favorites = fruits;
console.log(favorites); // ["banana", "orange", "apple"]
favorites[3] = "tomato"; // yes tomato is a fruit :)
console.log(fruits); ["banana", "orange", "apple", "tomato"]
// a fruit was added and is updated everywhere
```


## Type conversion

```javascript
35 / "5"; // 7
"35" / "5"; // 7
"35" + "5"; // 355
"35" + 5; // 355
35 + "5"; // 355
35 + 5; // 40
(+"35") + (+"5"); // 40
(+"35abc") + (+"5"); // NaN
parseInt("35abc") + 5; // 40
```


## Scope 

```javascript
var a = 100, // global scope
    b = a; // global scope
console.log(a); // 100 

b += 10; // we add 10 to b using the unary operator
console.log(b); // 110

function addAB() {
  var b = 5; // local scope
  // by preceding b with the var keyword
  // it became a local variable to the function addAB()
  // a in the outside scope is accessible by the function
  // so is equal 100
  return (a + b); // 105
}    
var sum = addAB(); // the value of sum will always be 105
console.log(sum);
```


## Scope (cont)
```javascript
var a = 100, b = a;
function addAB() {
  var b = 5; // b local scope
  function addIt() {
    var a = 95; // a local scope to addIt
    if (a > 90 ) {
      var b = 20; 
      // if this condition checks b has changed again
      // but conditional blocks do not hold a scope
    }  
    // so the new b is still accessible inside the addIt function
    return (a + b);
  }
  return addIt(); // 115
} 
var sum = addAB(); // sum will be 115
console.log(sum);   
```



# Conditional Statements
1. if / else
2. if else if if
3. And Or
3. Ternary operator
4. Switch


## If / else

```javascript
var A = "5",
    B = 5;
/**
 * Be careful what operator you want to use to compare values
 * the double equal (==) compares values only 
 * but does not compare types so "5" == 5 is true
 * even though the first one is a string and the second a number
 */
if (A == B) {
  console.log("A is a "+typeof A +" B is a "+typeof B);
} 
else {
  console.log("A and B are not equal")
}   
```


```javascript
/**
 * Here we are using the triple equal (===)
 * that essentially says to compare the equality
 * of the values and their types so in this case
 * "5" === 5 will be false since the two types differ
 */
var A = "5",
    B = 5;
if (A === B) {
  console.log("A is a "+typeof A +" B is a "+typeof B);
} 
else {
  console.log("A and B are not equal")
}   
```



# Loops
1. for
2. for in
3. while
4. do while
5. to break or to continue
6. recursion (functions)