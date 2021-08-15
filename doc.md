# TERMINAL COMMANDS

Creating a new local repository and GitHub repository\
`mkdir folder && cd folder` - makes a new directory and switches to it\
`git init` - initializes a new repo in this directory\
Create a new repo with the same name in GitHub\
Grab the SSH url from GitHub\
`git remote add origin URL` - ensures that the local repo and GitHub are in sync\
`git push -u origin master`

Adding/committing/pushing files\
`git add .`\
`git commit -m "Commit message"`\
`git push origin master`\
`git status`

Installing Mocha and Chai for testing\
`mkdir project_directory && cd project_directory`\
`npm init` - installs package.json\
`npm install mocha chai --save-dev` - installs Mocha and Chai\
In package.json, replace: 
```js
"scripts": {
    `"test": "./node_modules/mocha/bin/mocha"
```
Replacing the script will enable us to run `npm test`\
`gitignore node_modules` - Mocha and Chai wont get added to git repo

Cloning a forked gist\
`git clone git@gist.github.com:YOUR_FORKS_ID.git lunch`

Lint a program\
`eslint app.js`\
`eslint .`\ 

List
`ls` - list files in the directory \
`ls -l` - list files in long format\
`ls -a` - list files including hidden files

Removing a directory\
`rm -rf path/to/your/gist/directory`

Check content type\
`curl -i ipinfo.io`

# WEEK 1 - DAY 1 (1)

### Gists
What is a gist? It is another git repository.\
Except it's smaller and used for sharing smaller snippets of code.\
Gists cannot be given names.

### Fork
A fork is a GitHub operation.\
Where a user creates their own copy of another GitHub's user's existing repository.\
Forked repo links back to the original.\
However the forked one is fully controllable by the user that created that fork.

Terminal command:\
`git clone git@gist.github.com:YOUR_FORKS_ID.git lunch`

command - git clone\
SSH link - git@gist.github.com:YOUR_FORKS_ID.git\
directory name - lunch

### Linting
Linting helps us fix code inconsistencies.\
Analyzes code to see what errors, bugs, stlistic errors, and suspicious constructs are present.

Terminal command:\
`eslint app.js`\
`eslint .`

### Command Line Args
Command line arguments are strings of text passed through the CLI (terminal)\
Simplest way of retrieving arguments in node is via the process.argv array.\

VS Code syntax:\
`const args = process.argv;` - what you include in your code

Terminal command:\
`node app.js tom jack 43` - what you input in your terminal

### Library
Library is a collection of pre-written code.

### console.assert
console.assert() method writes an error message to the console if the assertion is false.\
`console.assert(1 === 1.1);` // => prints out "Assertion failed" to the terminal

If the assertion is true, nothing happens.\
`console.assert(1 === 1);` // => nothing happens because true

# WEEK 1 - DAY 2 (2)

### Pseudocode
Understanding the problem and translating the program/code to a more human-like explanation.

Problem:\
`Write a program that prints the numbers from 100 to 200 to the console...`

Pseudocode:\
`Loop from 100 to 200:`\
`  Let num = the current step in the loop`\
`  If num % 3 is equal to 0 and num % 4 is equal to 0:`\
`    Print "LoopyLighthouse"`\
`  Else if num % 3 is equal to 0:`\
`    Print "Loopy"`\
`  Else if num % 4 is equal to 0:`\
`    Print "Lighthouse"`\
`  Otherwise`\
`    Print num`\
`  End if`\
`End loop`

### Ternary Operators
Shorthand for if/else conditional statement

Syntax:\
`condition ? exprIfTrue : exprIfFalse`

if/else conditional:
```javascript
function testNum(a) {
  let result;
  if (a > 0) {
    result = 'positive';
  } else {
    result = 'NOT positive';
  }
  return result;
```

ternary operator:
```javascript
function testNum(a) {
  let result;
  a > 0 ? return 'positive' : 'NOT positive'
}
```

### Function Rules

1. Give your functions precise verb/action based names
2. Use camelCasedNames (like this one)
3. Properly indent the function code
4. Functions should focus on a single task: returning a value or causing a side effect. Break your function into additional smaller functions if you find it doing two or more things.
  1. One single task could be to compute and return a value
  2. Another single task could be to perform a side effect such as logging a message to the screen
5. It is ideal if functions try to avoid reading outer scope variables. If a function needs some information / data, then that data should instead be passed in as a parameter, making it available within the function's inner scope.

### Scope
Two levels of scope: global and local\
Global scope is available everywhere in the code.\
Local scope would only be available within the function in which it's defined.\
Scoping can overwrite variables

Example:
```javascript
let myGlobalVar = "global";

const printMyVars = function() {
  let myLocalVar = "local";
  console.log("-- Inside printMyVars --");
  console.log("myLocalVar is:", myLocalVar);
  console.log("myGlobalVar is:", myGlobalVar);
}
```

### Errors
Syntax Error - incorrect programming syntax (no ;, no +, no }, etc.)\
Reference Error - incorrect variables/functions (typed lasName instead of lastName)\
Type Error - the function cannot work as it is a different class type (Array.isArray("hello") = won't work, Array.isArray needs to work with arrays)

### Coercion (Truthy/Falsey)
`===` compares two values including the class type\
`12 === "12"` false. numbers != string\
`==` forces the two values to be the same type\
`12 == "12"` true

Falsey values:
```javascript
0 == false;
"" == false;
null == false;
undefined == false;
NaN == false;
```

# WEEK 1 - DAY 3 (3)

### Data Types
Primitives: when you access a primitive type you work directly on its value.
1. String
2. Number
3. Boolean
4. Undefined
5. Null
6. Symbol

Objects are not primitive! (arrays, objects, functions, etc).

Complex: when you access a complex type you work on a reference to its value.
1. Object
2. Array
3. Function

### Objects
Objects:
* contain key-value pairs; each key maps to a value (color: purple)
* contain keys which are always strings
* have unique keys; same key cannot appear twice
* have keys point to values which can be any type (color: undefined)

Bracket Notation:\
When accessing an object property using brackets, the key must be in quotes. Otherwise it would be considered a variable name isntead of a string literal.

```javascript
const person = { firstName: "Khurram" };
person[firstName]; // ReferenceError: firstName is not defined
person['firstName']; // "Khurram
```

```javascript
const person = { firstName: "Khurram" };
const propertyName = "firstName";
const firstName = person[propertyName]; // interpreted as person["firstName"]
```

```javascript
const person = {
  name: "Paul",
  address: {
    street: "310 W 95th",
    city: "New York",
    zipCode: 10027
  }
};
person["address"]["city"]; // => "New York"
```

for...in loop:\
Iterates through an object
```javascript
var planetMoons = {
  mercury: 0,
  venus: 0,
  earth: 1,
  mars: 2,
  jupiter: 67,
  saturn: 62,
  uranus: 27,
  neptune: 14
};

for (var planet in planetMoons) {
  var numberOfMoons = planetMoons[planet];
  console.log("Planet: " + planet + ", # of Moons: "+ numberOfMoons);
}
```

# WEEK 1 - DAY 4 (4)

### First-class Object
An object with no restrictions on its creation, destruction, or usage.\
This includes the ability to be passed as an argument, returned from a function, and assigned to a variable.\

### Function as Objects
Functions can be stored in variables and passed around.\
Functions can do everything that other objects can do (like having properties assigned to them).

### Higher Order Functions
Functions that take in callbacks.\
Functions that operate on other functions, either by taking them as arguments or by returning them.\
Example: forEach, filter

```
// coolArrowFunction is a Higher Order Function
const coolArrowFunction = () => console.log('pouet')

// doSomethingMultipleTimes is NOT a HOF
const doSomethingMultipleTimes = (callback, nbOfTimes) => {
  for(let i = 0; i < nbOfTimes; i++){
    callback()
  }
}

doSomethingMultipleTimes(coolFunction, 10)
```

### forEach
![forEach](https://cdn.discordapp.com/attachments/857321916066168832/868864087818383441/image0.jpg)

### Callback Functions
Higher order functions\
Functions that you send into other functions.\
Most notable usage of having function as values.\
Callback is when a function (reference) passed into another function (receiver).\
Receiver function is accepting behaviour to perform by calling the callback function that it now has access to.\
Receiver function can decide to call the callback function at any time, as many times as it wants.

```
const coolArrowFunction = () => console.log('pouet')

// doSomethingMultipleTimes needs a callback function
const doSomethingMultipleTimes = (callback, nbOfTimes) => {
  for(let i = 0; i < nbOfTimes; i++){
    callback()
  }
}

// coolArrowFunction is a Callback function
doSomethingMultipleTimes(coolFunction, 10)
```

Why do we use callback functions?\
Callbacks allow single-threaded operations to execute asynchronously.\
It helps the program to be more error-free, as each function does one job versus a big chunk of code that does multiple things in one function.

### Synchronous and Asynchronous Programming

Synchronous calls are coordinated; the call doesn't return until the sub-computation is finished.\
Asynchronous calls don't give you coordination, so you need a callback. You can't assume anything about the order in which things happen between two things that are asynchronous.

### Anonymous Functions
Functions that are often declared while being passed in as callbacks to other functions.

### Arrow Functions
Arrow functions provide a new syntax for declaring anonymous functions.\
Arrow functions don't get assigned a value for 'this'.

Code:
```javascript
// BEFORE: anonymous callback as function expression 
[1,2,3].forEach(function (num) {
  console.log('num: ', num);
});

// AFTER: anonymous callback as arrow function
[1,2,3].forEach((num) => {
  console.log('num: ', num);
});

// MORE REFACTORING
[1,2,3].forEach(num => console.log('num: ', num));
//Output: num: 1, num: 2, num: 3
```

### Vim
Vim Cheat Sheet:\
![Vim Cheat Sheet](http://www.viemu.com/vi-vim-cheat-sheet.gif)

# WEEK 1 - DAY 5 (5)

## this

### Recursion

To start figuring out how to solve a problem using recursion, it's helpful to first figure out the base case and the recursive case. 

The recursive case is when the function will continue to call itself. Every time the function calls itself, the input gets closer and closer to the base case.

The base case involves no calls to itself.

The base case is simply when the function doesn't make any recursive calls.

### Packages

Packages are self-contained code libraries that we can install and use in our projects.

# WEEK 1 - DAY 6 (6)

# WEEK 2 - DAY 1 (7)

### TDD
Test Driven Development\

### BDD
Behaviour Driven Development

### Mocha
A testing framework

### Chai
An assertion library\
Assertions are used to describe the desired outcome of our code\
Chai offers three different interfaces: `should`, `expect`, and `assert`

Example:
```javascript
// should
myVar.should.be.a('string');
myVar.should.equal('hello world');

// expect
expect(myVar).to.be.a('string');
expect(myVar).to.equal('hello world');

// assert
assert.typeOf(myVar, 'string');
assert.equal(myVar, 'hello world');
```

Chai Assertion Library - https://www.chaijs.com/
Chai: Differences - https://www.chaijs.com/guide/styles/#differences

### Asynchronous Programming
Asynchronous programming is when a unit of work is run separately from the main thread of the program and notifies the program of its completion.\
Asynchronous programming allows us to start a long running process, execute other code, and then perform some operation once the running long process has completed

### Blocking Code
Code that takes a long time to execute and blocks other code from executing

# WEEK 2 - DAY 2 (8)

### setTimeout()
A function to be executed after the timer expires.

Syntax:
```javascript
// setTimeout(function, delay)
// delay = 1000ms
setTimeout(function(){ console.log("Hello"); }, 3000);

setTimeout(function() { 
  console.log("Hello"); 
  }, 3000);

// arrow function
setTimeout(() => { 
  console.log("Hello"); 
  }, 3000);

// Output:
// *waits for 3 seconds*
// Hello
```

### process.stdout.write
Process standard output\
Continuously prints the information as the data being retrieved and doesn't add a new line

Example:
```javascript
setTimeout(() => { 
  process.stdout.write("Hello"); 
  }, 3000);

// Output:
// HelloDiannes-MacBook-Air:lighthouse-web-n

// To fix the Hello and add a newline between Hello and the next prompt, add \n:
setTimeout(() => { 
  process.stdout.write("Hello\n"); 
  }, 3000);

// Output:
// Hello 
// Diannes-MacBook-Air:lighthouse-web-notes
```

### \r
We can use the special character \r to return our cursor back to the beginning of the line that we were on.

Example:
```javascript
process.stdout.write('hello from spinner1.js... \rheyyy\n');

// Output:
// heyyy from spinner1.js...
// instead of hello from spinner1.js...
```

### process.stdout.write('\x07');
This code performs a system sound when triggered

### User Events
An event is a custom piece of information about something your user does.\
Every event is assigned to a user who triggers it and it's visible on his or her timeline along with its attributes. For example, "User clicked the buy now button" or "User filled out a form".\
Can occur any time while our app is running

### process.stdin.on
Process standard input\
Use the 'on' method on stdin to register a callback

Syntax:
```javascript
process.stdin.on(event: string | symbol, listener: Function)
// adds the listener function to the end of the listeners array for the event named eventName

// Enter any texts ( User input)
process.stdin.on('data', key => {
  console.log(`You typed ${key.toString()}`);
  process.exit();
});

// Output:
// *User enters 'Lighthouse'*
// Lighthouse
// You typed Lighthouse
// *program exits*

/*
process.stdin.on(); is a listener
it's listening for a 'data' event which is fired when a user hits enter on the keyboard. 
When .on() hears the event, you get to do something by supplying a callback (under the parameter 'key' which is the listener), which is console.log(`You typed ${data.toString()}`).
*/
```

### Terminate Program
`'\u0003'` = CTRL + C\
`process.exit();`

Example:
```javascript
process.stdin.on('data', key => {
  console.log(`You typed ${key.toString()}`);
  if (key === '\u0003') {
    process.exit();
  }
});

// Output:
// *User enters 'Lighthouse'*
// Lighthouse
// You typed Lighthouse
// *program will not exit automatically, as it will wait for a command that calls for termination*
// *User presses CTRL + C
// *program exits*
```

### Readline
The readline module provides an interface for reading data from a Readable stream (such as process.stdin) one line at a time.\
More info: (Readline Github)[https://github.com/nodejs/node/blob/master/doc/api/readline.md]

npm install readline

Example:
```javascript
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question('What do you think of Node.js? ', (answer) => {
  // TODO: Log the answer in a database
  console.log(`Thank you for your valuable feedback: ${answer}`);

  rl.close();
});

/*
Output:
What do you think of Node.js?
*User types 'Great!'*
What do you think of Node.js? Great!
Thank you for your valuable feedback: Great!
*program exits*
*/
```

### Asynchronous Return Value

Synchronous Code:
```javascript
console.log("(1) I should first")

setTimeout(() => {
  console.log('(2) hello there')
}, 2000)

console.log("(3) and I should still run before async code")
```

Asynchronouse Code:
```javascript
// getData is getting defined
const getData = (callback) => {
  // this line is hardcoded
  const runError = false;
  setTimeout(() => {
    const data = {
      weather: 'sunny'
    }

    if(runError) {
      callback("Whoops an error occured")
    } else {
      callback(null, data)
    }

  }, 2000)
}

// getData is getting invoked
getData((err, weatherData) => {
  if(err){
    return console.log(err)
  }
  console.log('my weather data is:', weatherData)
})

// if runError is set to false, getData will print
// if runError is set to true, runError will run and say "Whoops an error occured"
```

# WEEK 2 - DAY 3 (9)

### Network
A Network is when two or more computers are connected and can communicate with each other.

Example:\
Desktop connected to wireless router using cable\
Laptop connected to wireless routing using WiFi\
Printer connected to wireless router using cable

This is a network!

### HTTP
Hyper Text Transfer Protocol\
A protocol used to read and write "resources" (data) in a simple text-based manner.

5 out of the 9 HTTP Request Methods:\
- GET: READ data from the server
- POST:  SEND data and CREATE an object on the server
- PUT/PATCH: generally used for editing existing data on the server
- DELETE: used to delete some existing data

HTTP is a request-response based protocol.\
A client makes a request to an HTTP server,\
immediately also sending a message asking for a specific resource,\
which the server sends down as a response.\
A server cannot send a response to a client if the client has not first sent a request.

### HTTP Paths and URL Structures
URL - Uniform Resource Locator

`http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#Somewhere`

Parts of a URL:\
- Protocol - `http`
- Domain (or Host) - `www.example.com`
- Port - `80`
- Resource Path - `path/to/myfile.html`
- Query Parameters - `key1=value1&key2=value2`
- Anchor - `#Somewhere`

### HTTP Responses
- Status Codes
- Body

### LAN
Local Area Network

Example:\
My home has a router with 5 devices connected to it.\
My home is in its own network, which is only local to my home.

### NIC
Network Interface Card
Acts as the ear and/or mouth of computer

### WAN
Wide Area Network

### MAC Address
Unique to each computer's NIC\
Serves as the computer's name\
MAC Address has 6 bytes long or 48 bits\
00:00:AB:13:5A:2C - 6 bytes\
You can combine 2 bytes at a time: 0000.AB13.5A2C

When computers want to reach out to another device,\
first it dials the MAC Address it wants to reach\
then, it indicates its own MAC Address\
lastly, the message itself

MAC B | MAC A | "Hello!"

### TCP
A network protocol\
Transmission Control Protocol\
Provides a standard protocol that allows machines to speak to each other.\
TCP based communication allows two machines to establish an open channel for two-way data communication.\
Once a connection is established, both parties can start sending and receiving data until one of them decides that it's had enough and decides to terminate the connection.

### IP Address
A specific number that one side dials to establish a connection to the other side.\
In a way, this is the phone number in the computer networking world.

### Ports
Kind of like phone number extentions.\
A computer can have many network-based applications running, much like how a company can have many different offices.

### Events
https://nodejs.org/api/stream.html#stream_event_data

# WEEK 2 - DAY 4 (10)

### JSON
JavaScript Object Notation\
JSON is a data format that underpins many modern web services\
A subset of the JavaScript language\
Language independent. Heavily used in other programming languages

JSON is built on two structures:\
* A collection of name/value pairs.\
* An ordered list of values.

Example:
```javascript
{
  "name": "New York City",
  "boroughs": [
    "Manhattan",
    "Queens",
    "Brooklyn",
    "The Bronx",
    "Staten Island"],
  "population": 8491079,
  "area_codes": [212, 347, 646, 718, 917, 929],
  "position": { "lat": 40.7127, "lng": -74.0059 }
}

//Note that the keys are always double-quoted "strings", and the values can be numbers, strings, or objects themselves.
```

### Serialization
Process of serialization converts objects into a string.\
Deserialization is the opposite, going from string to object.

### JSON.parse()
The JSON.parse() method parses a JSON string, constructing the JavaScript value or object described by the string.

Code:
```javascript
JSON.parse(text)
JSON.parse(text, reviver)
```

Demo:
```javascript
const json = '{"result":true, "count":42}';
const obj = JSON.parse(json);

console.log(obj.count);
// expected output: 42

console.log(obj.result);
// expected output: true
```

### JSON.stringify()
The JSON.stringify() method converts a JavaScript object or value to a JSON string, optionally replacing values if a replacer function is specified or optionally including only the specified properties if a replacer array is specified.

Code:
```javascript
JSON.stringify(value)
JSON.stringify(value, replacer)
JSON.stringify(value, replacer, space)
```

Demo:
```javascript
console.log(JSON.stringify({ x: 5, y: 6 }));
// expected output: "{"x":5,"y":6}"

console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)]));
// expected output: "[3,"false",false]"
```

### JSON Media Type

### API
Application Programming Interface
REST API - REpresentational State Transfer

### Promise
Another way to handle asynchronous operations in Javascript\
Returns an object because it is an object

The promise can exist in one of three states:\
- pending
- fulfilled = resolved
- failed = rejected

Readline Promise:
```
const readline = require('readline-promise').default;

const rlp = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
```

# WEEK 2 - DAY 5 (11)

### OOP
Object Orientation Programming\
A programming paradigm where objects are used to group data (properties) and behaviour (methods).

OOP's Goals:
- Code organization
- Re-usability (reduce duplicated code)
- Modurality (breaking code up into sensibly-divided units)

### Class
Simpler approach to Object Orientation (OO)\
Classes are blueprints/templates that are used to create instances of objects.\
A class describes what the object is going to be\
Create new objects using class

Example:
```javascript
class Pizza {
  // a class name should always be a noun
  // first letter should always be capitalized
}

let pizza1 = new Pizza();
let pizza2 = new Pizza();
// pizza1 and pizza2 are pizza objects
// When an object is created using a class, it is an INSTANCE of that class
// so pizza1 and pizza2 are instances of the Pizza class
```

### Methods and Properties

```javascript
class Pizza {

  constructor() {
    this.toppings = ["cheese"];
  }
  // constructor() is a method
  // toppings is a property

  addTopping(topping) {
    this.toppings.push(topping);
  }

}

Pizza.addTopping();
```

### Constructor
A special kind of method that gets executed when an object instance is created from a class.\
Everything inside the Pizza's constructor method will get run for the new instance of the class when `new Pizza()` is called.\
In other words, the constructor is for setting default values for any new object's properties.

### Inheritance
OOP technique\
Build a new class based on an existing class\
Use inheritance to reduce duplicate code and share behaviour (methods) between classes.

Duplication problem:
```javascript
class Student {
  // this constructor is identical to that of a mentor!
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }

  // here is a method that is specific to students
  enroll(cohort) {
    this.cohort = cohort;
  }

  // identical! Smells of code duplication
  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}

class Mentor {
  // this constructor is identical to that of a student!
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }

  // specific to mentors
  goOnShift() {
    this.onShift = true;
  }

  // specific to mentors
  goOffShift() {
    this.onShift = false;
  }

  // identical! Smells of code duplication
  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}
```

The Student and Mentor classes have identical constructor and bio methods.\
Student and Mentor inherit behavrious and state information from Person the keyword `extends`

```javascript
// This class represents all that is common between Student and Mentor
class Person {
  // moved here b/c it was identical
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }

  // moved here b/c it was identical
  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}

class Student extends Person {
  // stays in Student class since it's specific to students only
  enroll(cohort) {
    this.cohort = cohort;
  }
}

class Mentor extends Person {
  // specific to mentors
  goOnShift() {
    this.onShift = true;
  }

  // specific to mentors
  goOffShift() {
    this.onShift = false;
  }
}

// Student and Mentor are now subclasses of the Person class. Person is the superclass.
```

Example:
```javascript
class Plant {
  water() {
    console.log(`Watering the ${this.type}`);
    this.lastWatered = Date();
  }
}

class Flower extends Plant {
  constructor() {
    super()
    this.type = "flower";
  }
}

class Tree extends Plant {
  constructor() {
    super()
    this.type = "tree";
  }
}

class Bush extends Plant {
  constructor() {
    super()
    this.type = "bush";
  }
}

let bushy = new Bush;
bushy.lastWatered = Date()

console.log(bushy)

// Output:
// Bush {
//  type: 'bush',
// lastWatered: 'Sun Aug 01 2021 11:01:23 GMT-0400 (Eastern Daylight Time)' }

// Now if the water method changes, the code only has to be changed in one place
```

### Super
Another special keyword often found on OOP languages\
Explores the concept of method overriding

Example:
```javascript
// Super class
class Person {
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }

  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}

class Mentor extends Person {
  // Mentor bios need to include a bit more info
  bio() {
    return `I'm a mentor at Lighthouse Labs. ${super.bio()}`;
  }
}

// DRIVER CODE

const bob = new Mentor('Bob Ross', 'I like mountains way too much');
console.log(bob.bio());

// Output: I'm a mentor at Lighthouse Labs. My name is Bob Ross and here's my quirky fact: I like mountains way too much
```

### Getter and Setter Methods
Special methods\
Used to get the value of a property or set the value of a property

Use of getters and setters:
- Setters validate the data before assigning it to a property
- Getters compute a value on the fly instead of simply pulling it out of a property

```javascript
class Pizza {

  // ...

  // setSize now includes data validation
  setSize(size) {
    if (size === 's' || size === 'm' || size === 'l') {
      this.size = size;
    }
    // else we could throw an error, return false, etc.
    // We choose here to ignore all other values!
  }
}

// DRIVER CODE
let pizza = new Pizza();
pizza.setSize('s');
```

```javascript
class Pizza {

  // ...

  // replace our custom getters / setters with these ones!
  get price() {
    const basePrice = 10;
    const toppingPrice = 2;
    return basePrice + toppingPrice;
  }

  set size(size) {
    if (size === 's' || size === 'm' || size === 'l') {
      this._size = size;
    }
  }
}

let pizza = new Pizza();

pizza.price;      // instead of getPrice()
pizza.size = 's'; // instead of setSize(size)
console.log(pizza.size) // Output: undefined
console.log(pizza._size) // Output: s
```

### Abstraction
A technique for arranging complexity of computer systems. It works by establishing a level of complexity on which a person interacts with the system, suppressing the more complex details below the current level.

Example:\
In order to drive a car, the user must know how to use the foot pedals and steering wheel. The user does not necessarily need to know the engineering of a car in order to drive.

```javascript
class Pizza {
  constructor() {
    this.toppings = [];
  }
  addTopping(topping) {
    if (this.toppings.indexOf(topping) > -1) {
      // Topping already exists, deny!
      return false;
    }
    this.toppings.push(topping);
    return true;
  }
}

let pizza = new Pizza();

pizza.addTopping("cheese");
pizza.addTopping("mushrooms");

console.log(pizza)

// Output: 
// Pizza { toppings: [ 'cheese', 'mushrooms' ] }
```

### Private
Properties can be made `private`\
Which means that they can't be accessed outside of the class that they're created in.\
If `_` is added to the start of a property name, developers will know that they shouldn't access it directly.

```javascript
class Pizza {
  constructor() {
    this._toppings = [];
  }
  addTopping(topping) {
    this._toppings.push(topping);
  }
}

let pizza = new Pizza();

pizza.addTopping("cheese");
pizza.addTopping("mushrooms");
```

### Single Responsibility Principle
Single responsibility principle states that a class should be responsible for a single part of the app's functionality, giving it only one reason to change.\
To simplifly it, a class should only have one job.

# WEEK 2 - DAY 6 (12)

### cURL
cURL is a command line utility that is used to make HTTP requests to a given URL and it outputs the response.\
It allows you to see the URL.

Example:
`curl www.example.edu` - prints the html of the page\
`curl www.example.edu -i` - prints the response headers along with the html of the page

### DNS
Domain Name System

### Record Types
- A: most common; map a hostnames to IP address (IPv4, 32-bit address)
- NS: Name Server that is responsible for a DNS zone
- MX: Mail Exchange record specifies where email gets sent to
- CNAME: Canonical Name, an alias for another hostname
- AAAA: similar to A, but uses IPv6, 128-bit address

# WEEK 3 - DAY 1 (13)

### ExpressJS
1. Routine System
2. Templating Engine (ejs)
3. Middleware Functions

### Views
View = UI for the client\
Views are files that get sent out to the user or clients as response.

### Templates
Files that define the presentation of a web app's data separately from the server logic.

### CRUD
Create - Add a new record\
Read - Retrieve the value of a record\
Update - Update a record's value\
Delete - Delete a record

Example:\
Create - `users["5315"] = {first_name: "John", last_name: "Smith"}`\
Read - `users["5315"]`\
Update - `users["5315"].first_name = "Jane"`\
Delete - `delete users["5315"]`

HTTP Method and CRUD Action:\
POST - Create\
GET - Read\
PUT - Update\
DELETE - Delete

### Web 3-Tier Architecture

# WEEK 3 - DAY 2 (14)

### Cookies
A feature of HTTP\
HTTP server can tell a client to remember certain keys and values ("cookies")\
Small blocks of data created by a web server while a user is browsing a website and placed on the user's computer or other device by the user's web browser.\
In essence, the server can ask a client to "keep reminding" the server of the client's identity (or other information) with every subsequent request.

Example:\
A patient with their Insurance ID visits the doctor.\
A Chrome browser with their Cookie (key-value pair) visits the website (Amazon).

# WEEK 3 - DAY 3 (15)

# WEEK 3 - DAY 4 (16)

### REST
REpresentation State Transfer\
A set of conventions and practices in web development that deals with accessing and manipulating resources over HTTP.\
A pattern to organize endpoint structure\

CRUD => BREAD:\
B - Browse, GET method, /maps (I want to look at maps)\
R - Read, GET method, /maps/:id (I want to read a specific map from a city)\
E - Edit, POST method, /maps/:id\
A - Add, POST method, /maps\
D - Delete, POST method, /maps/:id/delete

Other methods:\
PUT - update a single resource in its entirety\
PATCH - update an attribute to a single resource
DELETE - delete a single resource

B - Browse, GET method, /maps (I want to look at maps)\
R - Read, GET method, /maps/:id (I want to read a specific map from a city)\
E - Edit, PUT/PATCH method, /maps/:id\
A - Add, POST method, /maps\
D - Delete, DELETE method, /maps/:id/

# WEEK 3 - DAY 5 (17)

### Trees
Data structure\

!(Node and Edges)[https://i.imgur.com/0DLZ1jI.png]

# WEEK 3 - DAY 6 (18)

### Stack
A stack often refers to the collection of technologies used in a given system.

TinyApp has the following stack:\
- Web Server: Node.js
- Middleware: Express
- Template Engine: EJS
- Database: None, just an "In-Memory Object"

MEAN Stack:\
- MongoDB
- Express
- Angular.js
- MongoDB

Full-Stack:\
Full-stack means developers who are comfortable working with both back-end and front-end technologies.\
Back-end is server-side technologies like web servers (Node.js), databases, and so forth.\
Front-end refers to the stuff a user sees and interacts with, such as HTML / CSS / JavaScript and all the associated considerations on client-side (or in the browser).

### jQuery

Why does jQuery exist?\
- Reason 1: Fixes Browser compatibility issues
- Reason 2: Cleaner API

# WEEK 4 - DAY 1 (19)
# WEEK 4 - DAY 2 (20)
# WEEK 4 - DAY 3 (21)
# WEEK 4 - DAY 4 (22)
# WEEK 4 - DAY 5 (23)

# WEEK 4 - DAY 6 (24)

### Database

### ER Diagram
Entity-Relationship Diagram\
Graphical representation of the data requirements for a database\
Takes all of the parts of a database and puts the information in a box in a line form.

5 Major Parts of ERD:\
- Entity
- Attribute
- Primary Key
- Relationship
- Cardinality

### Entity
Represents a person, place, or a thing that you want to track in a database.\
Each occurence of the entity is an entity instance\
Each one will be a record or the "row" in a table

Example:\
Student

### Attributes
Describes various characteristics about an individual entity\
Attributes don't have to be unique to each entity
These becomes the columns in the table

Example:\
First Name
Last Name

### Primary Key
An attribute or group of attributes that uniquely identifies an instance of the entity\
A special attribute that must be unique\
A primary key will uniquely identify each instance\
It will ensure no two rows will have the same value for that attribute

Example:\
Student ID

### Composite Key
Sometimes needed instead of a primary key

### Relationship
Describes how one or more entities interact with each other\
Verb is often used to describe the relationship\
Relationships can be between two or more instances of entities. Sometimes an instance isn't needed.

Example:\
Student 123 has a phone\
Student 456 has no phone

### Cardinality
The count of instance that are allowed or are necessary between entity relationships.

Two Parts of Cardinality:\
- Minimum - represents the minimum number of instances that are required in the relationship
- Maximum - represents the maximum number of instances that are allowed

### Crow's Foot Notation
A way to represent a cardinality

![Crow's Foot Notation](https://www.codeproject.com/KB/architecture/878359/extracted-png-image1.png)

# WEEK 5 - DAY 1 (25)
# WEEK 5 - DAY 2 (26)
# WEEK 5 - DAY 3 (27)
# WEEK 5 - DAY 4 (28)
# WEEK 5 - DAY 5 (29)
# WEEK 5 - DAY 6 (30)

# WEEK 6 - DAY 1 (31)
# WEEK 6 - DAY 2 (32)
# WEEK 6 - DAY 3 (33)
# WEEK 6 - DAY 4 (34)
# WEEK 6 - DAY 5 (35)
# WEEK 6 - DAY 6 (36)

# WEEK 7 - DAY 1 (37)
# WEEK 7 - DAY 2 (38)
# WEEK 7 - DAY 3 (39)
# WEEK 7 - DAY 4 (40)
# WEEK 7 - DAY 5 (41)
# WEEK 7 - DAY 6 (42)

# WEEK 8 - DAY 1 (43)
# WEEK 8 - DAY 2 (44)
# WEEK 8 - DAY 3 (45)
# WEEK 8 - DAY 4 (46)
# WEEK 8 - DAY 5 (47)
# WEEK 8 - DAY 6 (48)

# WEEK 9 - DAY 1 (49)
# WEEK 9 - DAY 2 (50)
# WEEK 9 - DAY 3 (51)
# WEEK 9 - DAY 4 (52)
# WEEK 9 - DAY 5 (53)
# WEEK 9 - DAY 6 (54)

# WEEK 10 - DAY 1 (55)
# WEEK 10 - DAY 2 (56)
# WEEK 10 - DAY 3 (57)
# WEEK 10 - DAY 4 (58)
# WEEK 10 - DAY 5 (59)
# WEEK 10 - DAY 6 (60)

# WEEK 11 - DAY 1 (61)
# WEEK 11 - DAY 2 (62)
# WEEK 11 - DAY 3 (63)
# WEEK 11 - DAY 4 (64)
# WEEK 11 - DAY 5 (65)
# WEEK 11 - DAY 6 (66)

# WEEK 12 - DAY 1 (67)
# WEEK 12 - DAY 2 (68)
# WEEK 12 - DAY 3 (69)
# WEEK 12 - DAY 4 (70)
# WEEK 12 - DAY 5 (71)
# WEEK 12 - DAY 6 (72)

https://jsfiddle.net/dtremblay/p71v9mwb/656