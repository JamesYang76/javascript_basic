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
console.log(foo.nickname);//undefined

//for add new property
foo.nickname = 'James';
foo['age'] = 18;

//for delete property
delete foo.nickname;
delete foo['age'];
```
