# frontend-notes

# Heading 1

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6

Normal text

[Github](https://www.github.com)

_Italic text here_

**Bold text here**

~~Strikethrough text~~

![imagename](https://www.google.com/imgres?imgurl=https%3A%2F%2Fscx1.b-cdn.net%2Fcsz%2Fnews%2F800a%2F2015%2F2-dostarsmove.jpg&imgrefurl=https%3A%2F%2Fphys.org%2Fnews%2F2015-02-stars.html&tbnid=mHGQAQZKb4FguM&vet=10CDUQMyh9ahcKEwjY7aKY4q_wAhUAAAAAHQAAAAAQAg..i&docid=19KTAI7ALuXl9M&w=500&h=500&q=stars%20image&ved=0CDUQMyh9ahcKEwjY7aKY4q_wAhUAAAAAHQAAAAAQAg)

| Name | Email            | Address  |
| ---- | ---------------- | -------- |
| John | john@example.com | Address1 |

> Your quote looks like this.

```Let a = 2;

```

---

1. Item 1
2. Item 2
3. Item 3
   - Sub item 1
   - Sub item 3

- Unordered item
- Unordered item
- Unordered item

---

# Tech round 1

### HTML

| Name                                                                     | Email                                                                                         |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| The <div> tag is a block level element                                   | The <span> tag is an inline element.                                                          |
| It is best to attach it to a section of a web page.                      | It is best to attach a CSS to a small section of a line in a web page.                        |
| This tag should be used to wrap a section, for highligting that section. | This tag should be used to wrap any specific word that you want to highlight in your webpage. |

- Elements such as <header>, <nav>, <section>, <article>, <aside>, and <footer> act more or less like <div> elements. They group other elements together into page sections.

https://www.freecodecamp.org/news/semantic-html5-elements/#:~:text=Semantic%20HTML%20elements%20are%20those,content%20that%20is%20inside%20them.

### CSS

- https://rananitesh99.medium.com/five-css-interview-questions-you-will-be-asked-every-time-72fff69ecde

### JS

**How JS works**

1. Everything inside JS happens in Execution context.
2. JS is synchoronous single threaded language which means JS only execute one line at a time maintaing the order.
3. Inside EC we have two phase

- Memory creation(Variable environment) - allocates memory to all variables and function. Here the special keyword _undefined_ is assigned to variables declared using var keyword. For functions whole code is being assigned. Values are assigned in key value pair.
- Code Execution(Thread of execution) - Here JS skims through the code and work accordingly

4.  Wnenever we invoke a function EC is created.
5.  Call stack is the stack of EC.
6.  Global EC is created as soon as program is run.
7.  As soon as EC is created it is pushed into stack.
8.  As soon as EC is deleted it is popped out from stack.

**copy objects**

```
const person = {
    firstName: 'John',
    lastName: 'Doe'
};


// using spread ...
let p1 = {
    ...person
};

// using  Object.assign() method
let p2 = Object.assign({}, person);

// using JSON
let p3 = JSON.parse(JSON.stringify(person));
```

- Both spread (...) and Object.assign() perform a shallow copy while the JSON methods carry a deep copy.

```
let obj1 = {
  fname: "amnah",
  lname: "khatun",
  address: {
    city: "Jamshedpur"
  }
};

let obj2 = { ...obj1 }; //shallow copy

obj2.fname = "elon";
obj2.address.city = "new york";
console.log(obj1, "obj1"); // { fname: 'amnah', lname: 'khatun', address: { city: 'new york' } }
console.log(obj2, "obj2"); // { fname: 'elon', lname: 'khatun', address: { city: 'new york' } }
```

- seal() and freeze() is used to prevent modification of an object.

**Promises**

https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

- Promises are one of the ways we can deal with asynchronous operations in JavaScript.
- A promise is an object which can be returned synchronously from an asynchronous function. It will be in one of 3 possible states:

1. Fulfilled: onFulfilled() will be called (e.g., resolve() was called)
2. Rejected: onRejected() will be called (e.g., reject() was called)
3. Pending: not yet fulfilled or rejected

- The main difference between Callback Functions and Promises is that we attach a callback to a Promise rather than passing it.

```
const wait = time => new Promise(resolve => setTimeout(resolve, time));

wait(3000).then(() => console.log("Hello"));
```

Callback hell

```
firstRequest(function(response) {
    secondRequest(response, function(nextResponse) {
        thirdRequest(nextResponse, function(finalResponse) {
            console.log('Final response: ' + finalResponse);
        }, failureCallback);
    }, failureCallback);
}, failureCallback);
```

with promise

```
firstRequest()
  .then(function(response) {
    return secondRequest(response);
}).then(function(nextResponse) {
    return thirdRequest(nextResponse);
}).then(function(finalResponse) {
    console.log('Final response: ' + finalResponse);
}).catch(failureCallback);
```

Promise with reject and resolve

```
let myPromise = new Promise((resolve, reject) => {
let condition;
if(condition is met){
resolve('Success')
} else {
reject ('Rejection')
}
})

myPromise.then(
  (message)=>{console.log(message)
}).catch((error)=>{
  console.log(error)
})
```

- async ensures that the function returns a promise.
- The keyword await makes JavaScript wait until that promise settles and returns its result.
- We may get this error if we forget to put async before a function. As stated earlier, await only works inside an async function.

* Promise.reject() returns a rejected promise.
* Promise.resolve() returns a resolved promise.
* Promise.race() takes an array (or any iterable) and returns a promise that resolves with the value of the first resolved promise in the iterable, or rejects with the reason of the first promise that rejects.
* Promise.all() takes an array (or any iterable) and returns a promise that resolves when all of the promises in the iterable argument have resolved, or rejects with the reason of the first passed promise that rejects.

**Event propagation**

https://medium.com/@marjuhirsh/event-propagation-event-delegation-7d3db1baf02a#:~:text=Event%20delegation%20takes%20advantage%20of,event%20listeners%20to%20specific%20nodes.&text=If%20a%20page%20would%20have,up%20a%20lot%20of%20memory.

Event propagation happen in 3 phases

1. Capturing
2. Target
3. Bubbling

there are two types og Event propagation

- Event bubbling (Goes from child to parent to grandparent, used by microsoft)
- Event capturing (Goes from grandparent to parent to child, used by netscape)
- If it’s false or omitted, then the handler is set on the bubbling phase.
- If it’s true, then the handler is set on the capturing phase.

```
document.querySelector('#button1).addEventListener('click', (e) => {
  console.log('triggered)
}, true)
```

##### Event delegation

- Event delegation takes advantage of event propagation and so, allows the event listener to be set on a parent element.
- The blur, focus, load and unload events don’t bubble like other events.

**Chaining on conditional operator**

```
function dummy(param){
  return condition1 ? value1
       : condition2 ? value2
       : condition3 ? value 3
       : value4;
}

//same as
function dummy(param){
if(condition1){return value1;}
 else if(condotion2){return value2};
 else if(condotion3){return value3};
 else {return value4}
}

```

**Call bind and apply**

- call and apply are used for function borrowing.
- We can borrow function from one object and use it with data of another object.

```
let obj1 = {
  "fname" : "amnah,
  "lname" : "khatun"
}

function printFullName(greet){
  console.log(this.fname + this.lname + greet);
}

let obj2 = {
  "fname" : "elon,
  "lname" : "musk"
}

printFullName.call(obj1, "Hi")
printFullName.call(obj2, "Hello")
printFullName.apply(obj2, ["Hello")]

1st argument is reference to this
rest argument are parameter to function

- call and apply directly invokes the method

- bind returns the copy of the method which can be called later.
let x = printFullName.bind(obj2, "Hola")
-bind returns a function which can be invoked later

we can call bind using currying and closure

let add = function(a,b){
  return a + b;
}

let addTwo = add.bind(this,2)
let addThree = add.bind(this,3)

```

**Hoisting**
Hoisting is a phenomenon where we can access variables and functions before initializig it.

```
Lexical environment = local memory + lexical env of its parent
```

- lexical means heirarchy or in sequence
- inner function is lexically inside outer function

**Scope**

var - refers to same memory location
var b = 100;
{
var b =10;
console.log(b) ==> 10
}
console.log(b) ==> 10
shadows and update the global variable

let b = 200
{
let b = 20;
console.log(b) ==> 20 [Block memory space]
}
console.log(b) ==> 200 [script memory space]
let & const are stored in different memory location

**closures**

- closure is function bundled together with its lexical environment.
- functions even after being returned remember their scope because of closure.
- function remembers the reference to the variable.

Use of closure

- Currying
- encapsulation
- memoize and once
- setTimeouts

**custom MAP method**

```
const arr = ["1","2","3"];
Array.prototype.myMap = function (cb){
  let newArr = [];
  for(let arr of this){
    newArr.push(cb(arr))
  }
  return newArr;
}
arr.myMap((item) => console.log(item * 2))
```

### React

**props vs state**
| Props | state |
| ---- | ---------------- |
| Props are read only (immutable) |State can be modified using setState() |
| Props are used to pass data to components |State are maintained inside a component |

- React uses unidirectional data flow. Data can be passed from parent to child.
- Props can pass functions that may manipulate state. We can store the state in the parent and allow its child to use and manipulate the state.

**HOC**

https://codesandbox.io/s/a-simple-higher-order-component-forked-lk8gq?file=/index.js

- A HOC takes a component as input parameter and returns a new component.
- We don’t modify or mutate the component. We create new ones.
- A HOC is used to compose components for code reuse.
- A HOC is a pure function. That means it has no side effects. It only returns a new component.

```
const Hello = ({name}) => <h1>Hello {name}</h1>

function simpleHOC (WrappedComponent){
  return class extends React.Component {
    render(){
      <WrappedComponent {...props}/>
    }
  }
}

const NewComponent = simpleHOC(Hello);

const App(){
  <NewComponent name ="Hello" >
}

```

- Reuse component logic

```
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

https://www.smashingmagazine.com/2020/06/higher-order-components-react/

Eg of HOC

- PROVIDE COMPONENTS WITH SPECIFIC STYLING

#### Hooks

`const [count, setCount] = useState(0);`

- It combines the componentDidMount, componentDidUpdate and componentWillUnmount.

- To run the useEffect on first render and on every update, no need to pass 2nd argument.
- To call the method only when something changes, pass the second argument.
- To mimic componentWillUnmount, useEffect may return a function that cleans up after it.
- We can have mutiple effects in the same component.

### Redux

**core concept of redux**

- Single source of truth.
- State is read only(state can only be changed by dispatching action, and actions are objects).
- Pure reducers(reducers are pure function which based on the action return the updated state. Reducers cant modify the state they return the updated state object)
