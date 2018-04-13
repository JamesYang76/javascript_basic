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
#### Array-like objects
```javascript
var obj = { name:'foo',length:1};
obj.push('baz');//error
Array.prototype.push.apply(obj,['baz']);//2
console.log(obj);//{1: "baz", name: "foo", length: 2}
```

