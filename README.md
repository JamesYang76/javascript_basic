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
#### Copy an Array 
```javascript
//slice(start index, end index -1)
var fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];
fruits.slice();// ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
fruits.slice(2);//["Lemon", "Apple", "Mango"]
fruits.slice(2,3);//["Lemon"]
fruits.slice(1, -2);//["Orange", "Lemon"]
fruits;// ["Banana", "Orange", "Lemon", "Apple", "Mango"]
```

#### map
The map() method creates a new array with the results of calling a provided function\
on every element in the calling array.
```javascript
var numbers = [1, 4, 9];
var doubles = numbers.map(function(num) {
  return num * 2;
});
```
#### filter
The filter() method creates a new array with all elements\
that pass the test implemented by the provided function.
```javascript
function isBigEnough(value) {
  return value >= 10;
}
var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]
```

#### forEach/reduce
```javascript
var numbers = [1, 4, 9];
numbers.forEach(function(element) {
  console.log(element);
});

var sum = [0, 1, 2, 3].reduce(function (accumulator, currentValue) {
  return accumulator + currentValue;
}, 0); //6

var sum = [0, 1, 2, 3].reduce(function (accumulator, currentValue) {
  return accumulator + currentValue;
}, 4); //10
```

#### includes
The includes() method determines whether an array includes a certain element,\
returning true or false as appropriate.
```javascript
var pets = ['cat', 'dog', 'bat'];
console.log(pets.includes('cat'));// expected output: true
console.log(pets.includes('at'));// expected output: false
```

#### Array to String
``` javascript
var a = ['Wind', 'Rain', 'Fire'];
a.join();      // 'Wind,Rain,Fire'
a.join(', ');  // 'Wind, Rain, Fire'
a.join(' + '); // 'Wind + Rain + Fire'
a.join('');    // 'WindRainFire'
```
#### Array-like objects
```javascript
var obj = { name:'foo',length:1};
obj.push('baz');//error
Array.prototype.push.apply(obj,['baz']);//2
console.log(obj);//{1: "baz", name: "foo", length: 2}
```

### String
#### String to Array
```javascript
var myString = 'Hello World. How are you doing?';
var splits = myString.split(' ', 3);
console.log(splits);//["Hello", "World.", "How"]
var splits = myString.split(' ');
console.log(splits);//["Hello", "World.", "How", "are", "you", "doing?"]
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

//when innner function called, this is bind to window 
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
#### scope
scope is defined when function,with,catch are made.
```javascript
var value ="value1";
function printFunc() {
   var value = "value2";
   function printVal() {
     return value;
   }
console.log(printVal());
}
printFunc();//"value2"

var value ="value1";
function printVal() { return value;}
function printFunc(Func) {
   var value = "value2";
   console.log(Func());
}
printFunc(printVal);//"value1"


function printFunc() {
  myG ="global G";
}
myG;//erro
printFunc();
myG;//"global G";
```
#### property
```javascript
function Person(name) {
   this.name = name;
}
var foo = new Person('bar');
foo.name;//'bar'

//becasue of no new, this point to window.
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
#### constructor and prototype
A function has prototype which poiont to a prototype object\
A prototype object has a connstrutor which point to the function
```javascript
function Person(name) {
   this.name = name;
}
/*
Person        |              |      
  prototype --|------------->| prototype object 
              |<-------------|--construtor
*/
```

### Object
#### Define
```javascript
var foo = new Object();
foo.name = 'foo';
foo.__proto__;//Object()

var bar = { name :'bar'};
bar.__proto; //Object()

function Person(name) {
   this.name = name;
}
var you = new Person('you');
you.__proto__;//Person()
```

#### Prototype chaining
A function(constructor)'s prototype and object's _proto_ point to the same object which is the prototype object.\
When read/write properties, a object can go up to _proto_ and check proporties if the object has no properties.
```javascript
function Person(name) {
   this.name = name;
}
var foo = new Person('foo');
var bar = new Person('bar');
Person.prototype.getName = function() { return this.name };
Person.prototype.country = 'nz';
foo.getName();//"foo"
foo.country;//"nz"
bar.country;//"nz"
foo.country = "US";
bar.country;//"nz"
```

#### instanceof
The instanceof operator tests whether the prototype property of a constructor appears anywhere\
in the prototype chain of an object.
```javascript
function Person(name) {
   this.name = name;
}
var foo = new Person('foo');
console.log(foo instanceof Person); //true
console.log(foo instanceof Object); //true

function Person(name) {
   if(!(this instanceof arguments.callee))
      return new Person(name);
   this.name = name;
}
var foo = Person('foo');
var foo = new Person('foo');
```
#### hasOwnProperty
This method can be used to determine whether an object has the specified property\
as a direct property of that object
```javascript
function Person(name) {
   this.name = name;
}
var foo = new Person('foo');
foo.hasOwnProperty('name'); //true
foo.hasOwnProperty('toString');//false
```
#### call/apply/bind
```javascript
var obj = {name:"James"};
window.name = 'Global';
var greeting = function(town){
    return "welcome "+this.name+ " in " + town;
};

greeting.call(obj,"Newtown");//"welcome James in Newtown"
greeting.apply(obj,["Newtown"]);//"welcome James in Newtown"
greeting.apply();//"welcome Global in undefined"
greeting.bind(obj)("Wellinton"); //"welcome James in Wellinton"
```
### Inheritance

#### traditional 
```javascript
function Person() {
  this.name = 'anonymous';
  this.sayHello = function () {
      console.log(this.name);
  }
}
function Unikys() {
  var obj = new Person();
  obj.name = "Unikys";
  obj.job = "Nothing";
  return obj;
}

var unikys = new Unikys();
unikys.sayHello();//"Unikys"

unikys instanceof Person;//true
unikys instanceof Unikys;//false
```
#### using prototype
```javascript
function Person() {
  this.name = 'anonymous';
  this.sayHello = function () {
      console.log(this.name);
  }
}
function Unikys() {
  this.name = "Unikys";
}
Unikys.prototype = new Person();
unikys instanceof Person;//true
unikys instanceof Unikys;//true
```
#### using Object.create
```javascript
/*
Object.create = function (o) {
   function F() {}
   F.prototype = o;
   return new F();
}
*/

var person = {
   name : 'anonymous',
   sayHello:function() {
     console.log(this.name);
   }
};

var unikys = Object.create(person);
unikys.name ='Unikys';
unikys.sayHello();//"Unikys"
unikey instanceof person; //error
person.isPrototypeOf(unikys));//true
Object.getPrototypeOf(unikys) === person;//true

```
### Loop

#### for in
```javascript
var person = {
   name : 'anonymous',
   sayHello:function() {} };

var unikys = Object.create(person);
for (var i in unikys) {
   console.log("unikys["+i+"] = "+ unikys[i]);
}
```



### Closuer
The function points to a variable in outer function.
```javascript
var add = (function () {
    var counter = 0;
    return function () {return counter += 1;} //<-------closure
})();
add();//1
add();//2
```
#### Private method
```javascript
var counter = (function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  };   
})();
console.log(counter.value()); // logs 0
counter.increment();
counter.increment();
console.log(counter.value()); // logs 2
counter.decrement();
console.log(counter.value()); // logs 1


var makeCounter = function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  }  
};
var counter1 = makeCounter();
var counter2 = makeCounter();
alert(counter1.value()); /* Alerts 0 */
counter1.increment();
counter1.increment();
alert(counter1.value()); /* Alerts 2 */
counter1.decrement();
alert(counter1.value()); /* Alerts 1 */
alert(counter2.value()); /* Alerts 0 */
```
#### Watch out
```javascript
for(var i = 1; i <=4; i++) {
   setTimeout(function() { console.log(i)}, i*1000);
}

for(var i = 1; i <=4; i++) {
   (function(currentI) {
      setTimeout(function() { console.log(currentI)}, currentI * 1000);
   })(i);
}
```
