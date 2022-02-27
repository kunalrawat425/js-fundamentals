# js-fundamentals
Here is the detailed explanation and recap to your concepts
//declarations - let, const and var  -DOne
//function, expression and arrow functions  -DOne
// arrays, string methods  -DOne
//Settimeout and setInterval  -DOne
//rest and spread operator  -DOne
// Classes
//scope, lexical scope and closure
//call back, promises and async/await -DOne
// modules,import and export
console.clear();

//let and const cannot be redeclared,hoisted and are block scoped
// var is global and have no scope

var fname = "kunal";
var fname = "dwadwa";

let mname = "laxman";
// let mname = "laxman"; cannot be redclared

const lname = "rawat";
//  lname = ""; cannot be redclared and cannot be changed

let string = "kunal";
{
  let string = "dwa";
  console.log(string);
}

// let string="kunal";
// {
//   string = 'dwa';
//   console.log(string);
// }

console.log("out of scope", string);

//Hoisting
// Js hoists only declaration, not initialization
console.log(x);
var x = 10;
console.log(x);

//function types
first();
function first() {
  console.log("I am a global function and can be called before declaration");
}

let functionExpression = function () {
  console.log("I am function expression and can be fired after declaration");
};

functionExpression();

let arrowFunction = () => "I love Js";

console.log(
  "Single line arrow function and returns bydefault " + arrowFunction()
);

let arrowFunctionParam = (param) => param;
let arrowFunctionParams = (param1, param2) => param1 + param2;

console.log(
  "Single line arrow function and returns bydefault " + arrowFunctionParam(10)
);

console.log(
  "Single line arrow function and returns bydefault" +
    arrowFunctionParams(10, 20)
);

let multilineArrowFunction = () => {
  console.log("Multi line arrow function ");
  console.log("Second line");
  console.log("Third line");
};
multilineArrowFunction();

//Array Methods
// const array cannot be reassigned but elements can be changed
let arr = [10, 20, 30, 40, 50];
let obj = { fname: "kunal", mname: "kunal", lname: "rawat" };
arr.forEach((item, index) => {
  console.log(item, index);
});
// //For in used for object keys
// for(let ob in obj){
//   console.log(ob)
// }
// // for of overiterable array/string
// for(let ar of arr){
//   console.log(ar);
// }
// let string ="kunal laxmansingh rawat"
// for(let char of string){
//   console.log(char);
// }
console.log(arr.map((item) => item * 10));
console.log(arr.find((item) => item == 10));
console.log(arr.findIndex((item) => item == 10));
console.log(arr.filter((item) => item > 10));

//splice returns deleted element and alter array, can start index add and delete
console.log(arr.splice(0, 1));

console.log("new array " + arr);
console.log(arr.slice(0, 2));
console.log("new array " + arr);

//sting methods
let string = "I love Js";
console.log(string.split(""));
for (let char of string) {
  console.log(char);
}
console.log([...string]);

// Rest and spread
//Both uses same operator

//rest for accepting upto nth params i.e ...n (convert n params to array)

function rest(param1, param2, ...n) {
  console.log(param1, param2, n);
}

rest(1, 2, 3, 4, 5, 6, 7, 8, 9);

//Vice versa flow is spread i.e array to n params
console.log([...arr, ...arr]);

//callbacks

function callMeInFuture() {
  console.log("called");
}

function callBackTest(callbackReciever) {
  callbackReciever();
}
callBackTest(callMeInFuture);

//Promise either reject or resolve
//catch handles only synchronous errros .i.e avoid errors in setTimeout

let promise = new Promise(function (resolve, reject) {
  reject(45454); 
});
//goes either in resolve or reject and thenable/catch on error
promise
  .then(
    (res) => {
      console.log("IN resolved", res);
      return 6545;
    },
    (rej) => {
      console.log("IN reject", rej);
      return rej;
    }
  )
  .then((res) => {
    console.log("In first then", res);
    return res;
  })
  .then((res) => {
    console.log("In second then", res);
  })
  .catch((err) => {
    console.log("In first catch", err);
  });

//ASync functions return promise bydefault
async function Async() {
  // return "kunal";
}
console.log("async", Async());

Async().then(
  (value) => console.log(value),
  (err) => {}
);

// setTimeout
let timer1 = setTimeout(function () {
  console.log("calling after 2secs");
}, 2000);

let timer2 = setTimeout(function () {
  console.log("calling after 0secs");
});
clearTimeout(timer2);
