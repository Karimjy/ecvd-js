# JS - Node / Algo
*ECV Digital - 15/10/2015*

**Pre-requisites: you must read the Readme placed at the root folder to setup your computer**

---
# Welcome 
## The teacher: Morgan Giraud
![Morgan Giraud](https://en.gravatar.com/userimage/27393472/35e00906a5a12cd6a66616944e8d5edf.png?size=200)

[Linkedin](https://fr.linkedin.com/in/morgangiraud)
[Github](https://github.com/morgangiraud)

---
# Javascript
- Scripting language
- Async et callback !
- Let's have a look at the [standard](https://fr.wikipedia.org/wiki/ECMAScript)

--
# Browsers and javascript
See [how does that work](https://www.youtube.com/watch?v=ioXBf3FAJt8)

---

# Async Behaviors
Example: What is the output of this code ?
```javascript
// Example 1
setTimeout(function(){ // setTimeout is an async function
    console.log(1);    
},1000);
console.log(2);
```    
```
Output: 
- 2
- 1
``` 
<!-- .element: class="fragment" -->

--
## Async Behaviors - next
Example: What is the output of this code ?
```javascript
setTimeout(function(){
    console.log(1);    
},1000);
for(i=0;true;i++){
    console.log(2);    
}
```
```
Output:
- 2
- 2
- 2
...
```
<!-- .element: class="fragment" -->
You will never see the "1", Why ? <!-- .element: class="fragment" -->

The callback call has been added to the queue but the event loop doesn't have any "time" to check the queue<!-- .element: class="fragment" -->

--
### Async Behaviors - conclusion
A `for` Loop is a *synchronized* piece of code (or sync.)
> No other code will be able to run between two lines of synchronized type of code

The `setTimeout` function is an asynchronized function (or async.)

> Other code may execute between a function call and its callback call

From the JavasScript process viewpoint, every I/O is asynchronized

---

# NodeJS
- NodeJS Installation : `brew install nodejs`
- What is NodeJS
  - Let's look at the deps folder: https://github.com/nodejs/node/tree/master/deps
- Here is the doc: [Reference](https://nodejs.org/api/)

--
# Exercice
Write a very simple webserver
- Write a simpe webserver inside a `.js` file
- Run the file with NodeJS: `node server.js`
- Access you web server with a browser

--
# Exercice - next
Improve your webserver to read the query and serve files
- Parse the query to grab the filename
- use the `readFile` function in the `filesystem` package to access files locally
- Handle the case when a file is missing, return a 404 status

---

### Javascript injection for the lulz
- Create a file containing: 
```javascript 
  alert('I\'ve been injected');
```
- Launch your webserver
- Access your index file
- Open your browser console and type:
```javascript
s = document.createElement('script');
s.src = "injected.js";
existingScriptTag = document.getElementByTagName('script')[0];
existingScriptTag.parent.appendChild(s);
```

---

# Algorithmy
What is an [algorithm](https://fr.wikipedia.org/wiki/Algorithme) ?

First: Basic mathematic concept checkup
  - A sum: $\sum_{i=0}^n i = \frac{n(n+1)}{2}$
  - A limit: $\lim_{x\to 0}$
  - An equivalence: $f(n) \sim n$
  - A factorial: $n!$
  - A logarithm: $\log(x)$

--
# Exercice
What are the equivalence of those functions in $+\infty$
- $f(n) = n^6 + 3n \sim_?$
- $f(n) = 2^n + 12 \sim_?$
- $f(n) = 3^n + 2^n \sim_?$
- $f(n) = n^n + n \sim_?$

Note: 

---
# Complexity
What is a [complexity "theta of n": $\Theta(n)$](https://en.wikipedia.org/wiki/Analysis_of_algorithms#Evaluating_run-time_complexity) ?

A good [ressource](http://discrete.gr/complexity) to start !

--
## Fundamental instructions
You can count 1 for each of those
- Assigning a value to a variable `a = 0`
- Looking up the value of an element in an array `a[0]`
- Comparing two values `a > b`
- Incrementing a value `a++`
- Basic arithmetic operations such as addition and multiplication `+, -, /, *`

--
# Example
```javascript
// Given: A = [...] with n elements
var M = A[0];                   
for( var i = 0; i < n; ++i ) {   
  if( A[i] >= M ) {
    M = A[i];                   
  }
}
```
Result: $f( n ) = 4 + 2n + 4n = 6n + 4 \sim n$ <!-- .element: class="fragment" -->
> Complexity: $\Theta(n)$  

<!-- .element: class="fragment" -->

--
# Example
```javascript
var duplicate = false;
for( var i = 0; i < n; ++i ) {
  for ( var j = 0; j < n; ++j ) {
    if ( i != j && A[i] == A[j] ) {
      duplicate = true;
      break;
    }
  }
  if ( duplicate ) {
    break;
  }
}
```
> Complexity: $\Theta(n^2)$  

<!-- .element: class="fragment" -->

---
# Majoration: $O(n)$
We read it"Big O of n": 

## Example
```javascript
// Given: a = [...] with n elements
var b = [];
for(var i = 0;i < n;i++){
  var m = a[0];
  var mi = 0;
  a.forEach(function(element, i){
    if(element < m){
      m = element;
      mi = i;
    }
  });
  array.splice(mi, 1);
  b.push(m); 
}
```

--
You can say that: $\Theta(n) = \sum_{i=0}^n i$ but if you don't know how to calculate this formula it's clearly of no use

What can we do ?

----
We know that $ \Theta(n) = \sum_{i=0}^n i $ and $\forall i: i < n$ <!-- .element: class="fragment" -->

So we can say $ \Theta(n) < \sum_{i=0}^n n => \Theta(n) < n^2 $ <!-- .element: class="fragment" -->

In this case we say we have majored $\Theta(n)$ with $n^2$ <!-- .element: class="fragment" -->
> The $\Theta(n)$ algorithm is $O(n^2)$  

<!-- .element: class="fragment" -->