# javascript_basic

#### null and undefined
If a variable is not assgined by value, the variable is undefined and type is also undefined.\
If a variable is assgined by null, the variable is null, but type is object.
```javascript
var checkUndefined;
typeof checkUndefined;  //"undefined"
console.log(checkUndefined); // undefined
console.log(checkUndefined === undefined);//true
console.log(typeof checkUndefined === 'undefined'); //true

var checkNull = null;
typeof checkNull; //"object"
console.log(checkNull); //null
console.log(checkNull === null);//true
console.log(typeof checkNull === null);//false
```
#### !! operator
Change operand into boolean
```javascript
console.log(!!0);//false
console.log(!!null);//false
console.log(!!undefined);//false
console.log(!!{});//true
```
#### == and ===
In case of ==, if there are different types between two operands, make the same type.\
In case of ===, also compare types.
```javascript
console.log(1=='1');//true
console.log(1==='1');//false
```
#### read/write and add/delete object property
There are two ways: . and []\
If there is no property, undefined return
```javascript
var foo = {
   name :'foo',
   major : 'computer'
};
console.log(foo.name); //foo
console.log(foo['major']);//computer
console.log(foo[major]);//undefined
console.log(foo.nickname);//undefined

//for add new property
foo.nickname = 'James';
foo['age'] = 18;

//for delete property
delete foo.nickname;
delete foo['age'];

var obj = { 0:'foo',1:'bar'};
console.log(obj[0]);//'foo'
console.log(obj['0']);//'foo'

```
### Array
#### Array define
```javascript
var foo = new Array(3);
console.log(foo);//[undefined,undefined,undefined]
console.log(foo.length);//3

var bar = new Array("James","Best");
console.log(bar);//["James", "Best"]
console.log(bar.length);//2

var emptyArr = [];
var fooEmpty = new Array(0);
console.log(emptyArr);//[]
console.log(fooEmpty);//[]

var normalArry=[1,2,3];
console.log(normalArry);//[1,2,3]
```
#### Add/remove elements
```javascript
var emptyArr = [];
emptyArr[0] = 100;
emptyArr[1] = true;
console.log(emptyArr);//[100, true]
emptyArr[100] = false;
console.log(emptyArr.length);//101

var arr = ["first"];
arr.length = 3;
console.log(arr);// ["first", undefined,undefined]

var arr = ["zero","one"];
arr.push("two");
console.log(arr);//["zero", "one", "two"]

var last = arr.pop(); //"two"
console.log(arr);//["zero", "one"]
var first = arr.shift();//"zero"
console.log(arr);//["one"]

var newLength = arr.unshift("zero");//2
console.log(arr);////["zero", "one"]

var arr = ["zero","one","two"];
delete arr[2];
console.log(arr.length);//3
console.log(arr);//["zero", "one",undefined]


var fruits = ["Strawberry", "Banana", "Mango"];
var pos = fruits.indexOf('Banana'); //1
//splice(start index, delete count)
var removedItem = fruits.splice(pos, 1);//["Banana"]
console.log(fruits);//["Strawberry", "Mango"]
```
#### slice 
```javascript
//slice(start index, end index -1)
var fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];
fruits.slice();// ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
fruits.slice(2);//["Lemon", "Apple", "Mango"]
fruits.slice(2,3);//["Lemon"]
fruits.slice(1, -2);//["Orange", "Lemon"]
fruits;// ["Banana", "Orange", "Lemon", "Apple", "Mango"]

```
#### Array-like objects
```javascript
var obj = { name:'foo',length:1};
obj.push('baz');//error
Array.prototype.push.apply(obj,['baz']);//2
console.log(obj);//{1: "baz", name: "foo", length: 2}
```

### Function
#### function expression
```javascript
var factorialVar = function factorial(n) {
   if( n <= 1) return 1;
   return n * factorial(n-1); //only can access inner
};
factorialVar(3);//6
factorial(3);//error
```
#### function hoisting
```javascript
//for function statement
add(2,3); //5
fucntion add(x,y) {
   return x+y;
}

//for function expression
add(2,3);//error
var add = fucntion (x,y) {
   return x+y;
};
```
#### immediate function
```javascript
(function(name) {
    console.log("immediate function  = "+ name);
})('foo');//"immediate function  = foo"
```
#### arguments
```javascript
function func(a,b) {
  console.log(a,b);
}
func();//undefined undefined
func(1);//1 undefined
func(1,2,3);//1 2
func.length//2
```
arguments is the Array-like objects
 ```javascript
function sum() {
   var result =0;
   for (var i =0; i < arguments.length;i++) result += arguments[i];
   
   // change  Array-like objects into Array type
   var arg = Array.prototypes.slice.apply(arguments); 
   return result;
}
console.log(sum(1,2,3,4,5));//15
 ```
#### this
```javascript
//this is bind to myObj
var myObj = {
   name:'foo',
   sayName:function() {
      console.log(this.name); 
   }
};
myObj.sayName();//'foo'

//this is bind to window
var test = "This is a test";
console.log(window.test); //"This is a test"
 var sayFoo = function() {
   console.log(this.test);
 }
sayFoo();///"This is a test"

var value = 100;
var myObj = {
   value: 1,
   func1:function() {
      this.value += 1; //2 
      var func2 = function() { 
         this.value += 1; //101
         
         var func3 = function() {
            this.value += 1; //102
         }
         func3();
      }
      func2();
   }
};
```
#### constructor
```javascript
function Person(name) {
   this.name = name;
}
var foo = new Person('bar');
foo.name;//'bar'
Person('window name');
window.name;//'window name'
```
#### return
In javascript, function always return\
If there is no return, undefined returns\
If there is no return in constructor, object returns\
If return is not object in constructor,  object returns
```javascript
function testFn() {
 console.log(this.test);
}
var retVal = testFn();
retVal;//undefined

function Person(name) {
   this.name = name;
}
var foo = new Person("bar");

function Person(name) {
   this.name = name;
   return 10;
}
var foo = new Person("aaa");//Person {name: "aaa"}

function Person(name) {
   this.name = name;
   return {age:10};
}
var foo = new Person("aaa");//{age: 10}
```
