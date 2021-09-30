# Questions about closures
_General questions about closures_

## 1) What is a closure? ## 
It's a JS's feature where a function defined inside another function has access to the parent function's variables.


## 2) Give me an example of closure ## 
```
var super = "Batman";
function skulk() {
  var action = "skulking";
  function report() {
  var reportNum = 3;
  
    for (var i = 0; i < reportNum; i++ ) {
      console.log(super + " " + action + " " + i);
    }
   }
   report();
  }

skulk();
```
## 3) What is ()() in code? 
It's a "shortcut" to just execute the function without having to store the result in a variable.

## 4) Move the variable after the closure (the function inside the function) and explain what happens. ##
Nothing happens, since hoisitng is not affecting this part of code, because the execution is not yet happening, only the declarations.

## 5) Change var for let and explain why the logic is not affected. ##
It's not affected, because since nothing has been executed yet (only declared) there's still time to instatiate the variable.

## 6) Scope chain, an example of it, how many closures can we nest ##
It's a JS mechanism that tells us what variables can be accessed by a particular function, depending on **WHERE** we define our variables. We can nest infinite closures. Every closure has three scopes:
Local Scope (Own scope)
Outer Functions Scope
Global Scope

```
function a() {

    console.log(miVariable); //output: 1
}

function b() {
    var myVariable=2;
    a();
}

var myVariable= 1;

b()
```
## 7) Are there any conflicts between the closure and the global scope? ##
Only if you use them incorrectly. *Check the last example*

## 8) Advantages of closures.  ##
Protected access to the variables inside a scope and function factories (It creates functions that can add a specific value to their argument)

## 9) ¿What is data hiding and encapsulation?  ##
Data hiding: It's one of the main consequences of encapsulation. Basically, it is the ability of objects to shield variables from external access
Encapsulation: It is the ability of an object to be a container (or capsule) for its member properties, including variables and methods.

## 10) Give me an example of privacy with closures.   ##
```
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

var Counter1 = makeCounter();
var Counter2 = makeCounter();
console.log(Counter1.value()); 
Counter1.increment();
Counter1.increment();
console.log(Counter1.value()); 
Counter1.decrement();
console.log(Counter1.value()); 
console.log(Counter2.value()); 
```

## 11) What happens if you create two counters with the same closure?   ##
Nothing, they will be in different lexical envirenments and will not share memory.

## 12) How can we add more functions as a decrement counter? Give an example of it. ##
```
function counter() {
  let counter = 0;
  
  this.incrementCounter = () => {
    counter++;
    console.log(counter);
  }
  
  this.reduceCounter = () => {
    counter-;
    console.log(counter);
  }
}

const counter = new Counter();
counter.incrementCounter();
counter.reduceCounter();
```

## 13) What are the disadvantages of closures? ##
Its use will increase memory usage and improper use can easily cause memory leaks.




