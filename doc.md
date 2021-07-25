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
In package.json, replace `"scripts": {`
    `"test": "./node_modules/mocha/bin/mocha"`\
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

# WEEK 1 - DAY 1

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

# WEEK 1 - DAY 2

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

Falsey values:\
```javascript
0 == false;
"" == false;
null == false;
undefined == false;
NaN == false;
```

# WEEK 1 - DAY 3

### Primitive Data Types
1. String
2. Number
3. Boolean
4. Undefined
5. Null
6. Symbol

Objects are not primitve! (arrays, objects, functions, etc)

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

# WEEK 1 - DAY 4


### Recursion

To start figuring out how to solve a problem using recursion, it's helpful to first figure out the base case and the recursive case. 

The recursive case is when the function will continue to call itself. Every time the function calls itself, the input gets closer and closer to the base case.

The base case involves no calls to itself.

The base case is simply when the function doesn't make any recursive calls.

### Packages

Packages are self-contained code libraries that we can install and use in our projects.

### Vim
Vim Cheat Sheet:\
![Vim Cheat Sheet](http://www.viemu.com/vi-vim-cheat-sheet.gif)