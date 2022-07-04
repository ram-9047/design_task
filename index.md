Understand "this" keyword

Q1 & Q2)
1 - "this" inside global object
this.house = "window house";

2- "this" inside an object

let johnHouse = {
    house: "john's house";
}

3- "this" inside a method

let johnHouse = {
    house: "john's house";
    cleanHouse(){
        console.log(`cleaning ${this.house}`);
    }
}

4- "this" inside a function

let cleanHouse = function(){
    console.log(`cleaning ${this.house}`);
}
cleanHouse.call(johnHouse);

5- "this" inside a inner function

let cleanHouse = function(){
    let innerFunction = function(){
        console.log(`cleaning ${this.house}`)
    }
    innerFunction();
}

To execute sucessfully there are 3 ways
=> define "this" inside the function

let cleanHouse = function(){
    let that = this;
    let innerFunction = function(){
        console.log(`cleaning ${that.house}`)
    }
    innerFunction();
}

=> use call() method

let cleanHouse = function(){
    let innerFunction = function(){
        console.log(`cleaning ${this.house}`)
    }
    innerFunction.call(this);
}

=> use bind() method

let cleanHouse = function(){
    let innerFunction = function(){
        console.log(`cleaning ${this.house}`)
    }
    innerFunction.bind(this);
}

=> use arrow method

let cleanHouse = function(){
    let innerFunction = () => {
        console.log(`cleaning ${this.house}`)
    }
    innerFunction();
}

6- "this" inside a constructor

let createHouse = function(name){
    this.name = `${name}s house`;
}

let sonuHouse = new createHouse("Sonu")

7- "this" inside a class

class createHouse{
    constructor(name){
        this.name= `${name}s house`
    }
    cleanHouse(){
        ...
    }
}

Q3), Q4) ,Q5) & Q6)

class Student {
  static count = 0;
  constructor(name, age, phoneNumber, boardMarks) {
    (this.name = name),
      (this.age = age),
      (this.phoneNumber = phoneNumber),
      (this.boardMarks = boardMarks);
    this.constructor.count++;
  }
}

Student.prototype.eligiblity = () => {
  if (this.boardMarks > 40) {
    console.log("Eligible");
  } else {
    console.log("Not Eligible");
  }
};
let student1 = new Student("Raju", 23, 123, 34);
let student2 = new Student("Shaym", 25, 3456, 45);
let student3 = new Student("Babu Rao", 24, 2356, 34);
let student4 = new Student("Kabira", 26, 3646, 49);
let student5 = new Student("Sam", 22, 5678, 20);



Fat Arrow Function
Q1)
"use strict";

// before ES6
let square = function (a) {
  return a * a;
};

// after ES6 or Fat Arrow Function
let a = 4;
let newSquare = () => {
  return a * a;
};

//before ES6

let x = function () {
  this.val = 1;
  setTimeout(function () {
    this.val++;
    console.log(this.val);
  }, 1);
};
let xx = new x();
//This will print "Nan" because "this.val++", here "this" keyword only refers to its function which is "setTimeOut"
// not its parent function which is "x". There are 2 ways to solve this

// 1st method
let x = function () {
  this.val = 1;
  let that = this;
  setTimeout(function () {
    that.val++;
    console.log(that.val);
  }, 1);
};

//2nd Method
let x = function () {
  this.val = 1;
  setTimeout(()=> {
    this.val++;
    console.log(this.val)
  },1)
};

Q2)

Student.prototype.eligiblity = () => {
  if (this.boardMarks > 40) {
    console.log("Eligible");
  } else {
    console.log("Not Eligible");
  }
};

Q3)
student1.eligiblity()
student2.eligiblity()
student3.eligiblity()
student4.eligiblity()
student5.eligiblity()