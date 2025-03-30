***
![modern-js](../Images/modern-js.png)
***
##### Var, Let, Const
```javascript
var    //global-scope
let    //block-scope
const  //block-scope
/*-----------------------------------------------*/
console.log(x);  //undefined
var x = 10;
/*-----------------------------------------------*/
x = 10;          //assign
console.log(x);  //10
var x;           //declare
/*-----------------------------------------------*/
y = 10;
console.log(y);  //error! cannot access 'y' before initialization
let y;
/*-----------------------------------------------*/
z = 10;
console.log(z);  //error! cannot access 'y' before initialization
const z;
/*-----------------------------------------------*/
var x = 10;
var x = 11;
console.log(x);  //11
/*-----------------------------------------------*/
let y = 10;
let y = 11;
console.log(y);  //error! identifier 'y' has already been declared
/*-----------------------------------------------*/
var x;
x = 10;
x = 11;
/*-----------------------------------------------*/
let y;
y = 10;
y = 11;
/*-----------------------------------------------*/
const z;
z = 10;   //syntaxError: missing initializer in const declaration
z = 11;   //typeError: assignment to constant variable
```
***
##### Arrow Function
```javascript
/* Normal Function */
function funcName(){ //your code here! }

/*-----------------------------------------------*/

/* Arrow Function */
const funcName = () => { //your code here! }
/*-----------------------------------------------*/
const sayAge = (age) => {
   return age + 2 
};
console.log( sayAge(18) )   //20
/*-----------------------------------------------*/
const sayAge = (age) => age + 2
console.log( sayAge(18) )   //20
/*-----------------------------------------------*/
const sayAge = _ => "age"   //const x = "age";
console.log( sayAge() )     //age
```
***
##### Export & Import
```javascript
// class1.js
const func = () => {
   console.log("one man");
}
export default func;

/*-----------------------------------------------*/

// mainApp.js
import func from './class1.js'
func()  //one man
```
```javascript
// class1.js
const sayHello = () => {
   console.log("Hello!");
}
const sayBye = () => {
   console.log("Bye!");
}
export { sayHello, sayBye };

/*-----------------------------------------------*/

// mainApp.js
import { sayHello, sayBye } from './class1.js'
sayHello()  //Hello!
sayBye()    //Bye!
```
```javascript
// class1.js
export const sayHello = () => {
   console.log("Hello!");
}
export const sayBye = () => {
   console.log("Bye!");
}

/*-----------------------------------------------*/

// mainApp.js
import { sayHello, sayBye } from './class1.js'
sayHello()  //Hello!
sayBye()    //Bye!
```
```javascript
// class1.js
export const SERVER_NAME = "localhost";

/*-----------------------------------------------*/

// mainApp.js
import { SERVER_NAME } from './class1.js'
console.log(SERVER_NAME);  //localhost
```
```javascript
// class1.js
const SERVER_NAME = "localhost";
export default SERVER_NAME;

/*-----------------------------------------------*/

// mainApp.js
import SERVER_NAME from './class1.js'
console.log(SERVER_NAME);  //localhost
```
***
##### Classes
```javascript
class Car {
  color = "red";                                 //property
  printColor = _ => console.log(this.color);     //method
}

let car1 = new Car();      //new object from main class
car1.printColor();         //the usage of classes & objects   { red }
```
```javascript
class Car {
  color = "red";
  printColor = (color) => { console.log(color); }
}

let car1 = new Car();
car1.printColor(blue);     //blue - bec. it's a parameter
```
```javascript
// classes.js
class Car {
   color = "red";
   printColor = _ => console.log(this.color);
}
class Taxi {
   color = "yellow";
   printColor = _ => console.log(this.color);
}
export { Car, Taxi };

/*-----------------------------------------------*/

// mainApp.js
import { Car, Taxi } from './classes.js'
let car1 = new Car();
let taxi1 = new Taxi();
car1.printColor();         //red
taxi1.printColor();        //yellow
```
```javascript
// classes.js
class RED {
   printRED = () => {
      console.log("hello from RED class!");
   }
}
class Car extends RED {    //inheretence
   constructor( color = "green" ){  //default parameter
      super();     //before running 'constructor()' runs the 'extends' code
      this.COLOR = color;
   }
   color = "red";
   printColor = (color) => { console.log(this.COLOR); }
}
export default Car

/*-----------------------------------------------*/

// mainApp.js
import Car from './classes.js'
let myCar1 = new Car();
let myCar2 = new Car();
myCar1.printColor();         //green
myCar2.printColor("blue");   //green, bec. 'printColor' don't use parameter
myCar1.printRED();           //hello from RED class!
myCar2.printRED();           //hello from RED class!
```
```javascript
// classes.js
class RED {
   printRED = () => {
      console.log("hello from RED class!");
   }
}
class Car extends RED {    //inheretence
   constructor( color = "green" ){  //default parameter
      super();     //before running 'constructor()' runs the 'extends' code
      this.COLOR = color;
   }
   color = "red";
   printColor = () => { console.log(this.COLOR); }
}
export default Car

/*-----------------------------------------------*/

// mainApp.js
import Car from './classes.js'
let myCar = new Car('gray');   //this parameter is for constructor
myCar.printColor();            //gray
```
***
##### Spread Operator
```javascript
let newArray = [...lastArray, 0];              //old array + 'zero' item
let newObject = {...oldObject, name:"ahmed"};  //old object + 'name' attribute

/*-----------------------------------------------*/

let oldArray = [1,2,3,4,5]
console.log(oldArray);     //[ 1, 2, 3, 4, 5 ]
let newArray = [...oldArray]
console.log(newArray);     //[ 1, 2, 3, 4, 5 ]
let newArray = [...oldArray,6,7,8]
console.log(newArray);     //[ 1, 2, 3, 4, 5, 6, 7, 8 ]
let newArray = [-2,-1,0,...oldArray]
console.log(newArray);     //[ -2, -1, 0, 1, 2, 3, 4, 5 ]

/*-----------------------------------------------*/

let oldObject = {id:'1', name:'muhammad'}
console.log(oldObject);    //{ id: '1', name: 'muhammad' }
let newObject = {...oldObject}
console.log(newObject);    //{ id: '1', name: 'muhammad' }
let newObject = {...oldObject,age:'18'}
console.log(newObject);    //{ id: '1', name: 'muhammad', age: '18' }
let newObject = {age:'18',...oldObject}
console.log(newObject);    //{ age: '18', id: '1', name: 'muhammad' }
let newObject = {...oldObject,name:'ali'}
console.log(newObject);    //{ id: '1', name: 'ali' }

/*-----------------------------------------------*/

let sum = (...args) => {  //'...args' is an array of parameters
   return args.filter(item => item === 1);
}
console.log(sum(4,8,2,5,9,4,6));  //[   ]
console.log(sum(4,8,2,1,9,4,6));  //[ 1 ]
```
***
##### De-structuring
```javascript
//Destructuring: extracts element from arrays & objects etc..
const arr = [1,2,5,7];
const [num1] = arr;
console.log(num1);           //1
const [num1,num2] = arr;
console.log(num1,num2);      //1 2
const [,,num3,num4] = arr;
console.log(num3,num4);      //5 7

/*-----------------------------------------------*/

const ob = {id:'1',name:'muhammad',age:'18'}
const {name} = ob;
console.log(name);             //muhammad
const {id ,name} = ob;
console.log(id, name);         //1 muhammad
const {id ,name, age} = ob;
console.log(id ,name, age);    //1 muhammad 18
```
***
##### Primitive Types
```javascript
//Search -> primitive vs non-primitive
let num1 = 2;
let num2 = num1;
console.log(num2);   //2

/*-----------------------------------------------*/

let student = {
   name: "muhammad"
}
console.log(student);     //{ name: "muhammad" }
let newStudent = student;
console.log(newStudent);  //{ name: "muhammad" }
student.name = "ali";
console.log(newStudent);  //{ name: "ali" }

/*-----------------------------------------------*/

let student = {
   name: "muhammad"
}
let newStudent = {...student};
console.log(newStudent);  //{ name: "muhammad" }
student.name = "ali";
console.log(newStudent);  //{ name: "muhammad" }
```
***
##### Array Functions
```javascript
const arr = [1,2,3,4,5,6];
console.log(arr);      //[ 1, 2, 3, 4, 5, 6 ]
const newArr = arr.map((item)=>{
   return item === 3;
});
console.log(newArr);   //[ false, false, true, false, false, false ]
```
***
##### Array Simple Methods
```javascript
const arr1 = ['a','b','c','d','e','f'];
const arr2 = arr1.slice(2);
console.log(arr1);  //[ 'a', 'b', 'c', 'd', 'e', 'f' ]
console.log(arr2);  //[ 'c', 'd', 'e', 'f' ]
const arr2 = arr1.slice(2, 4);
console.log(arr1);  //[ 'a', 'b', 'c', 'd', 'e', 'f' ]
console.log(arr2);  //[ 'c', 'd' ]
const arr2 = arr1.slice(-1);
console.log(arr2);  //[ 'f' ]
const arr2 = arr1.slice(-2);
console.log(arr2);  //[ 'e', 'f' ]

/*-----------------------------------------------*/

const arr1 = ['a','b','c','d','e','f'];
const arr2 = arr1.splice(2);
console.log(arr1);  //[ 'a', 'b' ]
console.log(arr2);  //[ 'c', 'd', 'e', 'f' ]
const arr2 = arr1.splice(-1);
console.log(arr1);  //[ 'a', 'b', 'c', 'd', 'e' ]
console.log(arr2);  //[ 'f' ]

/*-----------------------------------------------*/

const arr1 = ['a','b','c','d','e','f'];
const arr2 = arr1.reverse();
console.log(arr1);  //[ 'f', 'e', 'd', 'c', 'b', 'a' ]
console.log(arr2);  //[ 'f', 'e', 'd', 'c', 'b', 'a' ]

/*-----------------------------------------------*/

const arr1 = ['a','b','c','d','e','f'];
const arr0 = [1,2,3,4];
console.log(...arr1 , ...arr0);   //a b c d e f 1 2 3 4
const arr1 = ['a','b','c','d','e','f'];
const arr0 = [1,2,3,4];
const arr2 = [...arr1 , ...arr0]
console.log(arr2);    //[ a, b, c, d, e, f, 1, 2, 3, 4 ]
const arr1 = ['a','b','c','d','e','f'];
const arr0 = [1,2,3,4];
const arr2 = arr1.concat([1,2,3,4])
const arr3 = arr1.concat(arr0)
console.log(arr2);    //[ a, b, c, d, e, f, 1, 2, 3, 4 ]
console.log(arr3);    //[ a, b, c, d, e, f, 1, 2, 3, 4 ]

/*-----------------------------------------------*/

const arr1 = ['a','b','c','d','e','f'];
const arr0 = [1,2,3,4];
const arr2 = arr1.concat(arr0)
console.log(arr2.join(' - '));  //a - b - c - d - e - f - 1 - 2 - 3 - 4
console.log(arr2.join(' 0 '));  //a 0 b 0 c 0 d 0 e 0 f 0 1 0 2 0 3 0 4
```
***
##### Array Methods 2
```javascript
const arr1 = [1,2,3,4,5,6,7]
const arr2 = arr1.map(item => item > 2);
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(arr2);  //[ False, Flase, True, True, True, True, True ]

/*-----------------------------------------------*/

const arr1 = [1,2,3,4,5,6,7]
const arr2 = arr1.map(item => {
   if(item > 2)
   {return True}
   else
   {return False}
});
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(arr2);  //[ False, False, True, True, True, True, True ]

/*-----------------------------------------------*/

const arr1 = [1,2,3,4,5,6,7]
const arr2 = arr1.map(item => {
   if(item > 2)
   {console.log(item)}
});
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(arr2);  //[ 3, 4, 5, 6, 7 ]

/*-----------------------------------------------*/

const arr1 = [1,2,3,4,5,6,7]
const arr2 = arr1.filter(item => item > 2);
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(arr2);  //[ 3, 4, 5, 6, 7 ]

/*-----------------------------------------------*/

const arr1 = [1,2,3,4,5,6,7]
const arr2 = arr1.reduce((total, current) => total + current);
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(arr2);  //28

/*-----------------------------------------------*/

const arr1 = [1,2,3,4,5,6,7]
const arr2 = arr1.reduce((total, current) => total + current, 0);
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(arr2);  //28

/*-----------------------------------------------*/

const arr1 = ['a','b','c','d','e','f']
const arr2 = arr1.reduce((total, current) => total + current);
console.log(arr1);  //[ 'a', 'b', 'c', 'd', 'e', 'f' ]
console.log(arr2);  //abcdef

/*-----------------------------------------------*/

const arr1 = ['a','b','c','d','e','f']
const arr2 = arr1.reduce((total, current) => total + current, 0);
console.log(arr1);  //[ 'a', 'b', 'c', 'd', 'e', 'f' ]
console.log(arr2);  //0abcdef

/*-----------------------------------------------*/

const arr1 = [1,2,3,4,5,6,7]
const firstValue = arr1.find(item => item > 3);
console.log(arr1);  //[ 1, 2, 3, 4, 5, 6, 7 ]
console.log(firstValue);  //4

/*-----------------------------------------------*/

const arr1 = [7,4,8,2,10,9,0,6,1,3,5,11]
const arr2 = arr1.sort();
console.log(arr1);  //[ 0, 1, 10, 11, 2, 3, 4, 5, 6, 7, 8, 9 ]
console.log(arr2);  //[ 0, 1, 10, 11, 2, 3, 4, 5, 6, 7, 8, 9 ]

/*-----------------------------------------------*/

const arr1 = [7,4,8,2,10,9,0,6,1,3,5,11]
const arr2 = arr1.sort((a,b)=>{
   if(a > b)
    return 1;   //more than 0, keep them!
   if(b > a)
    return -1;  //less than 0, reverse them!
});
console.log(arr1);  //[ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ]
console.log(arr2);  //[ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 ]

/*-----------------------------------------------*/

const arr1 = [7,4,8,2,10,9,0,6,1,3,5,11]
const arr2 = arr1.sort((a,b)=>{
   if(a < b)
    return 1;   //more than 0, keep them!
   if(b < a)
    return -1;  //less than 0, reverse them!
});
console.log(arr1);  //[ 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 ]
console.log(arr2);  //[ 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 ]

/*-----------------------------------------------*/

const arr1 = ['d','e','a','f','b','c']
const arr2 = arr1.sort();
console.log(arr1);  //[ 'a', 'b', 'c', 'd', 'e', 'f' ]
console.log(arr2);  //[ 'a', 'b', 'c', 'd', 'e', 'f' ]
```
***
##### Higher Order Functions
```javascript
//1. function accepts another function
//2. function returns another function

/*-----------------------------------------------*/

const lowerCase = (str) => {
   return str.toLowerCase();
}
console.log(lowerCase("MUHAMMAD"))  //muhammad

/*-----------------------------------------------*/

const lowerCase = (str) => {
   return str.toLowerCase();
}
const transform = (word, fn) => { //higher-order function
   return fn(word);
}
console.log(transform("MUHAMMAD",lowerCase))   //muhammad
//Note: callback function is the fuction written without '()' as prev clg.

/*-----------------------------------------------*/

const sayHi = (welcome) => {
   return () => {
      console.log(welcome);
   }
}
console.log(sayHi('Welcome Ali!'))  //[Function (anonymous)]

/*-----------------------------------------------*/

const sayHi = (welcome) => {
   console.log(welcome);
   return () => {}
}
console.log(sayHi('Welcome Ali!'))  //Welcome Ali! , [Function (anonymous)]

/*-----------------------------------------------*/

const sayHi = (welcome) => {
   return () => {
      console.log(welcome);
   }
}
const say = sayHi('Welcome Wael!');
console.log(sayHi('Welcome Ali!'));  //Welcome Ali! , [Function (anonymous)]
console.log(say);                    //[Function (anonymous)]

/*-----------------------------------------------*/

const sayHi = (welcome) => {
   console.log(welcome);
   return (name) => {
      console.log(name)
   }
}
const say = sayHi('welcome message!');
console.log(say('muhammad'));    //welcome message! , muhammad , undefined

/*-----------------------------------------------*/

const sayHi = (welcome) => {
   console.log(welcome);
   return (name) => {
      console.log(name)
   }
}
const say = sayHi('welcome message!');
console.log(say('ali'));
console.log(say('ahmed'));
console.log(say('sayed'));      //welcome message! , ali , ahmed , sayed

/*-----------------------------------------------*/

const sayHi = (welcome) => {
   console.log(welcome);
   return (name) => {
      console.log(`${welcome} ${name}`)
   }
}
const say = sayHi('Welcome!');
console.log(say('Muhammad'));   //Welcome! Muhammad
```
***
##### Promise, Asynchronous, Synchronous
```javascript
// JavaScript is a single-thread language {only one operation in same time}
// Single-Thread is a Synchronous task. عمليات متزامنه زي الطابور
// Multi-Threas is an Asynchronous task. عمليات غير متزامنه ومتوازيه

/*-----------------------------------------------*/

console.log("first");  //first
console.log("second"); //second
console.log("third");  //third

/*-----------------------------------------------*/

let myPromise = new Promise((success,error)=>{
	const x = 0;
	if(x===0)
	{ success('This is ok!'); }
	else
	{ error('This is error!'); }
});
myPromise();  //TypeError: myPromise is not a function
myPromise.then(
   (resolve) => console.log(resolve),  //print the 'success('This is ok!');'
   (reject) => console.log(reject)     //print the 'error('This is error!');'
);
   
/*-----------------------------------------------*/

let myPromise = new Promise((success,error)=>{
	const x = 0;
	if(x===0)
	{ success('This is ok!'); }
	else
	{ error('This is error!'); }
}).then(
   (resolve) => console.log(resolve),  //print the 'success('This is ok!');'
   (reject) => console.log(reject)     //print the 'error('This is error!');'
);
```
***
##### Multi-Promise
```javascript
// eat.then -> play.then -> sleep.then

let eat = True;
let play = True;
let sleep = True;
let eating = new Promise((success,error)=>{
	if(eat)
	{ success('Food is delecious!'); }
	else
	{ error('Where is my food?'); }
})
let playing = new Promise((success,error)=>{
	if(play)
	{ success('I played'); }
	else
	{ error('I did not play'); }
})
let sleeping = new Promise((success,error)=>{
	if(sleep)
	{ success('I slept'); }
	else
	{ error('I did not sleep'); }
})
eating.then(
   (resolve) => console.log(resolve), //prints 'success('Food is delecious!');'
   (reject) => console.log(reject)    //prints 'error('Where is my food?');'
);
playing.then(
   (resolve) => console.log(resolve), //prints 'success('I played');'
   (reject) => console.log(reject)    //prints 'error('I did not play');'
);
sleeping.then(
   (resolve) => console.log(resolve), //prints 'success('I slept');'
   (reject) => console.log(reject)    //prints 'error('I did not sleep');'
);

/*-----------------------------------------------*/

let eat = True;
let play = True;
let sleep = True;
let eating = new Promise((success,error)=>{
	if(eat)
	{ success('Food is delecious!'); }
	else
	{ error('Where is my food?'); }
})
let playing = new Promise((success,error)=>{
	if(play)
	{ success('I played'); }
	else
	{ error('I did not play'); }
})
let sleeping = new Promise((success,error)=>{
	if(sleep)
	{ success('I slept'); }
	else
	{ error('I did not sleep'); }
})
eating.then(
   (resolve) => {
      console.log(resolve)                         //'Food is delecious!'
      playing.then(
         (resolve) => {
            console.log(resolve)                   //'I played'
            sleeping.then(
                (resolve) => console.log(resolve), //'I slept'
                (reject) => console.log(reject)    //'I did not sleep'
            );
        },
         (reject) => console.log(reject)           //I did not play'
    );
},
   (reject) => console.log(reject)                 //'Where is my food?'
);
```
***
##### Async ,Await
```javascript
// Async -> function
// Await -> promise1, promise2, promise3, ...

let eat = True;
let play = True;
let sleep = True;
let eating = new Promise((success,error)=>{
	if(eat)
	{ success('Food is delecious!'); }
	else
	{ error('Where is my food?'); }
})
let playing = new Promise((success,error)=>{
	if(play)
	{ success('I played'); }
	else
	{ error('I did not play'); }
})
let sleeping = new Promise((success,error)=>{
	if(sleep)
	{ success('I slept'); }
	else
	{ error('I did not sleep'); }
})

const run = async () => {
   const eatMessage = await eating();
   console.log(eatMessage);
   const playMessage = await playing();
   console.log(playMessage);
   const sleepMessage = await sleeping();
   console.log(sleepMessage);
}

run();   //TypeError: eating is not a function

/*-----------------------------------------------*/

let eat = True;
let play = True;
let sleep = True;
const eating = () => {
   return new Promise((success,error)=>{
	if(eat)
	{ success('Food is delecious!'); }
	else
	{ error('Where is my food?'); }
})}
const playing = () => {
   return new Promise((success,error)=>{
	if(play)
	{ success('I played'); }
	else
	{ error('I did not play'); }
})}
const sleeping = () => {
   return new Promise((success,error)=>{
	if(sleep)
	{ success('I slept'); }
	else
	{ error('I did not sleep'); }
})}

const run = async () => {
   const eatMessage = await eating();
   console.log(eatMessage);
   const playMessage = await playing();
   console.log(playMessage);
   const sleepMessage = await sleeping();
   console.log(sleepMessage);
}

run();   //Food is delecious! , I played , I slept

/*-----------------------------------------------*/

let eat = True;
let play = False;
let sleep = False;
const eating = () => {
   return new Promise((success,error)=>{
	if(eat)
	{ success('Food is delecious!'); }
	else
	{ error('Where is my food?'); }
})}
const playing = () => {
   return new Promise((success,error)=>{
	if(play)
	{ success('I played'); }
	else
	{ error('I did not play'); }
})}
const sleeping = () => {
   return new Promise((success,error)=>{
	if(sleep)
	{ success('I slept'); }
	else
	{ error('I did not sleep'); }
})}

const run = async () => {
   try {
        const eatMessage = await eating();
        console.log(eatMessage);
        const playMessage = await playing();
        console.log(playMessage);
	    const sleepMessage = await sleeping();
	    console.log(sleepMessage);
   } catch(error) { console.log(error); }
}

run();   //Food is delecious! , I did not play

/*-----------------------------------------------*/

let eat = False;
let play = True;
let sleep = True;
const eating = () => {
   return new Promise((success,error)=>{
	if(eat)
	{ success('Food is delecious!'); }
	else
	{ error('Where is my food?'); }
})}
const playing = () => {
   return new Promise((success,error)=>{
	if(play)
	{ success('I played'); }
	else
	{ error('I did not play'); }
})}
const sleeping = () => {
   return new Promise((success,error)=>{
	if(sleep)
	{ success('I slept'); }
	else
	{ error('I did not sleep'); }
})}

async function run () {
   try {
        const eatMessage = await eating();
        console.log(eatMessage);
        const playMessage = await playing();
        console.log(playMessage);
	    const sleepMessage = await sleeping();
	    console.log(sleepMessage);
   } catch(error) { console.log(error); }
}

run();   //Where is my food?
```