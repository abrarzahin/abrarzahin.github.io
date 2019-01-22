---
layout: post
title: Learning JavaScript
date: 2019-01-16 19:30 -0500
---
JavaScript is a very powerful language. It can be used within any browser in the world. On top of that, it can be used to write server-side code using node.js.

# Intro
When using JavaScript inside the browser, we can change how the page looks like and how it behaves. In this tutorial, we will only focus on learning the language itself, and therefore we will only use one function to print out our results called "console.log".

{% highlight html %}
 console.log("Goodbye, World!");
 {% endhighlight html %}
# Variables 
Like almost every dynamic language, JavaScript is a "duck-typed" language, and therefore every variable is defined using the var keyword, and can contain all types of variables.

We can define several types of variables to use in our code:
{% highlight html %}
 var myNumber = 3;                   // a number
var myString = "Hello, World!"      // a string
var myBoolean = true;               // a boolean
 {% endhighlight html %}
A few notes:
In JavaScript, the Number type can be both a floating point number and an integer.
Boolean variables can only be equal to either true or false.
There are two more advanced types in JavaScript. An array, and an object. We will get to them in more advanced tutorials.
{% highlight html %}
 var myArray = [];                    // an array
var myObject = {};                  // an object
 {% endhighlight html %}
On top of that, there are two special types called undefined and null.
When a variable is used without first defining a value for it, it is equal to undefined. For example:
{% highlight html %}
 var newVariable;
console.log(newVariable); //prints undefined
 {% endhighlight html %}
However, the null value is a different type of value, and is used when a variable should be marked as empty. undefined can be used for this purpose, but it should not be used.
{% highlight html %}
 var emptyVariable = null;
console.log(emptyVariable);
 {% endhighlight html %}
 will print out null.
 # Arrays
JavaScript can hold an array of variables in an Array object. In JavaScript, an array also functions as a list, a stack or a queue.
To define an array, either use the brackets notation or the Array object notation:
{% highlight html %}
 var myArray = [1, 2, 3];
var theSameArray = new Array(1, 2, 3);
 {% endhighlight html %}

Addressing
We can use the brackets [] operator to address a specific cell in our array. Addressing uses zero-based indices, so for example, in myArray the 2nd member can be addressed with index 1. One of the benefits of using an array datastructure is that you have constant time look-up, if you already know the index of the element you are trying to access.
{% highlight html %}
 console.log(myArray[1]);      // prints out 2
 {% endhighlight html %}

Arrays in JavaScript are sparse, meaning that we can also assign variables to random locations even though previous cells were undefined. For example:

{% highlight html %}
 var myArray = []
myArray[3] = "hello"
console.log(myArray);
 {% endhighlight html %}
Array Elements
Because JavaScript Arrays are just special kinds of objects, you can have elements of different types stored together in the same array. The example below is an array with a string, a number, and an empty object.
{% highlight html %}
 var myArray = ["string", 10, {}]
 {% endhighlight html %}

 # Manipulating Arrays

Pushing and popping
Arrays can also function as a stack. The push and pop methods insert and remove variables from the end of an array.
For example, let's create an empty array and push a few variables.
{% highlight html %}
 var myStack = [];
myStack.push(1);
myStack.push(2);
myStack.push(3);
console.log(myStack);.
 {% endhighlight html %}
This will print out:
{% highlight html %}
 1,2,3
 {% endhighlight html %}
After pushing variables to the array, we can then pop variables off from the end.
{% highlight html %}
 console.log(myStack.pop());
console.log(myStack);
 {% endhighlight html %}
This will print out the variable we popped from the array, and what's left of the array:
{% highlight html %}
 3           // the result from myStack.pop()
 1,2         // what myStack contains now 
 {% endhighlight html %}

Queues using shifting and unshifting
The shift and unshift methods are similar to push and pop, only they work from the beginning of the array. We can use the push and shift methods consecutively to utilize an array as a queue. For example:
{% highlight html %}
 var myQueue = [];
myQueue.push(1);
myQueue.push(2);
myQueue.push(3);

console.log(myQueue.shift());
console.log(myQueue.shift());
console.log(myQueue.shift());.
 {% endhighlight html %}

Splicing
Splicing arrays in JavaScript removes a certain part from an array to create a new array, made up from the part we took out. For example, if we wanted to remove the five numbers from the following array beginning from the 3rd index, we would do the following:
{% highlight html %}
 var myArray = [0,1,2,3,4,5,6,7,8,9];
var splice = myArray.splice(3,7);

console.log(splice);        // will print out 3,4,5,6,7
console.log(myArray);       // will print out 0,1,2,8,9
 {% endhighlight html %}

After splicing the array, it will only contain the part before and after the splicing. The splice is equal to all the variables between 3 and 7 (inclusive), and the remainder of the array, which contains all variables between 0 and 2 (inclusive), and 8 to 9 (inclusive).

# Operators 

The addition operator
The + (addition) operator is used for both addition and concatenation of strings.
For example, adding two variables is easy:
{% highlight html %}
 var a = 1;
var b = 2;
var c = a + b;     // c is now equal to 3
 {% endhighlight html %}

The addition operator is used for concatenating strings to strings, strings to numbers, and numbers to strings:
{% highlight html %}
 var name = "John";
console.log("Hello " + name + "!");
console.log("The meaning of life is " + 42);
console.log(42 + " is the meaning of life");
 {% endhighlight html %}

JavaScript behaves differently when you are trying to combine two operands of different types. The default primitive value is a string, so when you try to add a number to a string, JavaScript will transform the number to a string before the concatenation.
{% highlight html %}
 console.log(1 + "1");   // outputs "11"
 {% endhighlight html %}

Mathematical operators
To subtract, multiply and divide two numbers, use the minus (-), asterisk (*) and slash (/) signs.
{% highlight html %}
 console.log(3 - 5);     // outputs -2
console.log(3 * 5);     // outputs 15
console.log(3 / 5);     // outputs 0.6
 {% endhighlight html %}

Advanced mathematical operators
JavaScript supports the modulus operator (%) which calculates the remainder of a division operation.
{% highlight html %}
 console.log(5 % 3);     // outputs 2
 {% endhighlight html %}

JavaScript also supports combined assignment and operation operators. So, instead of typing myNumber = myNumber / 2, you can type myNumber /= 2. Here is a list of all these operators:
{% highlight html %}
/=
*=
-=
+=
%=
JavaScript also has a Math module which contains more advanced functions:

Math.abs calculates the absolute value of a number
Math.exp calculates e to the power of a number
Math.pow(x,y) calculates the result of x to the power of y
Math.floor removes the fraction part from a number
Math.random() will give a random number x where 0<=x<1
And many more mathematical functions.
{% endhighlight html %}

# Conditions

The if statement
The if statement allows us to check if an expression is equal to true or false, and execute different code according to the result.
For example, if we want ask the user whether his name is "John", we can use the confirm function.
An example of an attribute is:
{% highlight html %}
 if (confirm("Are you John Smith?"))
{
    console.log("Hello John, how are you?");
} else {
    console.log("Then what is your name?");
}
 {% endhighlight html %}
 

It is also possible to omit the else keyword if we only want to execute a block of code only if a certain expression is true.

To evaluate whether two variables are equal, the == operator is used. There is also another equality operator in JavaScript, ===, which does a strict comparison. This means that it will be true only if the two things you are comparing are the same type as well as same content.
An example of an attribute is:
{% highlight html %}
 console.log("1" == 1); // true
console.log("1" === 1); // false
 {% endhighlight html %}
For example:
An example of an attribute is:
{% highlight html %}
 var myNumber = 42;
if (myNumber == 42)
{
    console.log("The number is correct.");
}
 {% endhighlight html %}
 
Inequality operators can also be used to evaluate expressions. For example:

An example of an attribute is:
{% highlight html %}
 var foo = 1;
var bar = 2;

if (foo < bar)
{
    console.log("foo is smaller than bar.");
}
 {% endhighlight html %}
 
Two or more expressions can be evaluated together using logical operators to check if two expressions evaluate to true together, or at least one of them. To check if two expressions both evaluate to true, use the AND operator &&. To check if at least one of the expressions evaluate to true, use the OR operator ||.

An example of an attribute is:
{% highlight html %}
var foo = 1;
var bar = 2;
var moo = 3;

if (foo < bar && moo > bar)
{
    console.log("foo is smaller than bar AND moo is larger than bar.");
}

if (foo < bar || moo > bar)
{
    console.log("foo is smaller than bar OR moo is larger than bar.");
}
 {% endhighlight html %}
 

The NOT operator ! can also be used likewise:

An example of an attribute is:
{% highlight html %}
 var notTrue = false;
if (!notTrue)
{
    console.log("not not true is true!");
}
 {% endhighlight html %}
 
The switch statement
The switch statement is similar to the switch statement from the C programming language, but also supports strings. The switch statement is used to select between more than two different options, and to run the same code for more than one option. For example:
An example of an attribute is:
{% highlight html %}
 var rank = "Commander";
switch(rank)
{
    case "Private":
    case "Sergeant":
        console.log("You are not authorized.");
        break;
    case "Commander":
        console.log("Hello commander! what can I do for you today?");
        break;
    case "Captain":
        console.log("Hello captain! I will do anything you wish.");
        break;
    default:
        console.log("I don't know what your rank is.");
        break;
}
 {% endhighlight html %}
 
In this example, "Private" an "Sergeant" both trigger the first sentence, "Commander" triggers the second sentence and "Captain" triggers the third. If an unknown rank was evaulated, the default keyword defines the action for this case (optional). We must use the break statement between every code block to avoid the switch from executing the next code block.

# Loops

The for statement--
JavaScript has two methods for running the same code several times. It is mainly used for iterating over arrays or objects. Let's see an example:

{% highlight html %}
 var i;
for (i = 0; i < 3; i = i + 1)
{
    console.log(i);
}
 {% endhighlight html %}
 This will print out the following: 0
                                    1
                                    2
 

The for statement in JavaScript has the same syntax as in Java and C. It has three parts:

Initialization - Initializes the iterator variable i. In this example, we initialize i to 0.
Condition - As long as the condition is met, the loop continues to execute. In this example, we check that i is less than 3.
Increment - A directive which increments the iterator. In our case, we increment it by 1 on every loop.
We can also write a shorter notation for the statement by inserting the variable definition inside the for loop and incrementing using the ++ operator.

{% highlight html %}
 for (var i = 0; i < 3; i++)
{
    console.log(i);
}
 {% endhighlight html %}
 
To iterate over an array and print out all of its members, we usually use the for statement. Here's an example:

{% highlight html %}
 var myArray = ["A", "B", "C"];
for (var i = 0; i < myArray.length; i++)
{
    console.log("The member of myArray in index " + i + " is " + myArray[i]);
}
 {% endhighlight html %}

This prints out the contents of the array:

{% highlight html %}
 The member of myArray in index 0 is A
The member of myArray in index 1 is B
The member of myArray in index 2 is C
 {% endhighlight html %}
Notice that we used the length property of an array, which returns the number of members in the array, so we know when to stop iterating.

The while statement
The while statement is a more simple version of the for statement which checks if an expression evaluates to true and runs as long as it says true.

For example:
{% highlight html %}
 var i = 99;
while (i > 0)
{
    console.log(i + " bottles of beer on the wall");
    i -= 1;
}
 {% endhighlight html %}
break and continue statements
The break statement allows to stop the execution of a loop. For example, we can create a loop that loops forever using while(true) and use the break statement to break inside the loop instead by checking that a certain condition was met.
{% highlight html %}
 var i = 99;
while (true)
{
    console.log(i + " bottles of beer on the wall");
    i -= 1;
    if (i == 0)
    {
        break;
    }
}
 {% endhighlight html %}

The continue statement skips the rest of the loop and jumps back to the beginning of the loop. For example, if we would want to print only odd numbers using a for statement, we can do the following:
{% highlight html %}
 for (var i = 0; i < 100; i++)
{
    // check that the number is even
    if (i % 2 == 0)
    {
         continue;
    }
    // if we got here, then i is odd.
    console.log(i + " is an odd number.");
}
 {% endhighlight html %}

 # Objects

 JavaScript is a functional language, and for object oriented programming it uses both objects and functions, but objects are usually used as a data structure, similar to a dictionary in Python or a map in Java. In this tutorial, we will learn how to use objects as a data structure. The advanced tutorials explain more about object oriented JavaScript.

To initialize an object, use curly braces:
{% highlight html %}
 var emptyObject = {};
var personObject = {
    firstName : "John",
    lastName : "Smith"
}
 {% endhighlight html %}
 

Member addressing
Members of objects can be addressed using the brackets operator [], very much like arrays, but just like many other object oriented languages, the period . operator can also be used. They are very similar, except for the fact that brackets return a member by using a string, in contrast to the period operator, which requires the member to be a simple word (the word should not contain spaces, start with a letter or use illegal characters).

For example, we can continue to fill the person object with more details:
{% highlight html %}
 var personObject = {
    firstName : "John",
    lastName : "Smith"
}
personObject.age = 23;
personObject["salary"] = 14000;
 {% endhighlight html %}
 


Iteration
Iterating over members of a dictionary is not a trivial task, since iterating over objects can also yield members who don't actually belong to an object. Therefore, we must use the hasOwnProperty method to check that the member in fact belongs to the object.
{% highlight html %}
 for (var member in personObject)
{
    if (personObject.hasOwnProperty(member))
    {
        console.log("the member " + member + " of personObject is " + personObject[member])
    }
}
 {% endhighlight html %}
 

This will eventually print out
{% highlight html %}
 the member firstName of personObject is John
the member lastName of personObject is Smith
the member age of personObject is 23
the member salary of personObject is 14000
 {% endhighlight html %}

 # Functions

 Functions are code blocks that can have arguments, and function have their own scope. In JavaScript, functions are a very important feature of the program, and especially the fact that they can access local variables of a parent function (this is called a closure).

There are two ways to define functions in JavaScript - named functions and anonymous functions.

To define a named function, we use the function statement as follows:

{% highlight html %}
 function greet(name)
{
    return "Hello " + name + "!";
}

console.log(greet("Eric"));  
 {% endhighlight html %}
 
In this function, the name argument to the greet function is used inside the function to construct a new string and return it using the return statement.

To define an anonymous function, we can alternatively use the following syntax:
 {% highlight html %}
 var greet = function(name)
{
    return "Hello " + name + "!";
}

console.log(greet("Zahin"));
 {% endhighlight html %}

# Pop-up Boxes

There are three types of pop-up boxes in javascript: confirm, alert, and prompt. To use any of them, type
{% highlight html %}
 confirm("Hi!");
prompt("Bye!");
alert("Hello");
 {% endhighlight html %}

Confirm boxes will return "true" if ok is selected, and return "false" if cancel is selected. Alert boxes will not return anything. Prompt boxes will return whatever is in the text box. Note: prompt boxes also have an optional second parameter, which is the text that will already be in the text box.

# Callbacks

Callbacks in JavaScript are functions that are passed as arguments to other functions. This is a very important feature of asynchronous programming, and it enables the function that receives the callback to call our code when it finishes a long task, while allowing us to continue the execution of the code.

For example:
{% highlight html %}
 var callback = function() {
    console.log("Done!");
}

setTimeout(callback, 5000);
 {% endhighlight html %}
 
This code waits 5 seconds and prints out "Done!" when the 5 seconds are up. Note that this code will not work in the interpreter because it is not designed for handling callbacks.

It is also possible to define callbacks as anonymous functions, like so:
 
 {% highlight html %}
 setTimeout(function() {
    console.log("Done!");
}, 5000);
 {% endhighlight html %}
 




