### QUESTION 1) Discuss in words something you learned in class today or this week.

This week we learned about react router, which is an API for react applications. React router uses dynamic routing, which is a form of routing that takes place as the app is rendering, not in a conventional method outside of the app.

It allows us build a single-page web application with navigation without the page refreshing as the user navigates. React Router uses component structure to call components, which display the appropriate information.

By preventing a page refresh, and using Router or Link, the flash of a white screen or blank page is prevented. This is one increasingly common way of having a more seamless user experience. React router also allows the user to utilize browser functionality like the back button and the refresh page while maintaining the correct view of the application.

---

### QUESTION 2) How does hoisting work in JavaScript?

During the creation phase, the JavaScript engine moves the variable and function declarations to the top of your code. This feature is known as hoisting in JavaScript.

**Declaring the variable count with the "var" keyword**

Variable hoisting means the JavaScript engine moves the variable declarations to the top of the script. For example, the following example declares the count variable and initialize its value to 1:

```
console.log(count)
var count = 1;
```

In this example, we reference the counter variable before the declaration. However, the first line of code doesn’t cause an error. The reason is that the JavaScript engine moves the variable declaration to the top of the script. Technically, the code looks like the following in the execution phase:

```
var count;

console.log(count); // undefined
count = 1;
```

During the creation phase of the global execution context, the JavaScript engine places the variable counter in the memory and initializes its value to undefined.

**Declaring the variable count with the "let" keyword:**

```
console.log(counter);
let counter = 1;
```

The JavaScript issues the following error:

"ReferenceError: Cannot access 'counter' before initialization
The error message explains that the counter variable is already in the heap memory. However, it hasn’t been initialized.

Behind the scenes, the JavaScript engine hoists the variable declarations that use the let keyword. However, it doesn’t initialize the let variables.
Notice that if you access a variable that doesn’t exist, the JavaScript will throw a different error:

```
console.log(alien);
let counter = 1;
```

Here is the error:
"ReferenceError: alien is not defined

**Functional Declaration vs Functional Expression**

Example:

A function declaration will console.log 'execute' even with function being called before it is initialized because of hoisting.

```
execute();

function execute() {
console.log('execute')
}
```

Result: It will log 'execute'

However with function expressions, if the function execute() is called before it is initialized you will get a reference error. It is similar to a constant or variable being used before it is being defined. It is not moved up to the top via hoisting.

```
execute();

const execute = function (){
console.log('execute')
}
```

Result: It will log a reference error: execute is not defined

---

### QUESTION 3) Why is setState() in React Async instead of Sync?

If state was to be updated synchronously, props are not, it means you can’t know props until you re-render the parent component. The objects provided by React (state, props, refs) are consistent with each other and if you introduce a synchronous setState you could introduce some bugs. Thus, no benefit in making the setState synchronous if other objects won’t reflect this update until it is re-rendered.

In addition, if the navigation is fast enough, flashing and immediately hiding a spinner causes a degraded UX (user experience). Imagine you have multiple levels of components with different async dependencies, you end up with a cascade of spinners flashing one by one. This is both visually unpleasant and makes your app slower in practice because of all the DOM reflows.

---

### QUESTION 4) How is the Virtual-DOM more efficient than Dirty checking?

In React, each of our components have a state. This state is like an observable. Essentially, React knows when to re-render the scene because it is able to observe when this data changes. Dirty checking is slower than observables because we must poll the data at a regular interval and check all of the values in the data structure recursively. By comparison, setting a value on the state will signal to a listener that some state has changed, so React can simply listen for change events on the state and queue up re-rendering.

The virtual DOM is used for efficient re-rendering of the DOM. This isn’t really related to dirty checking your data. We could re-render using a virtual DOM with or without dirty checking. In fact, the diff algorithm is a dirty checker itself.

---

### QUESTION 5) What is PureComponent? When to use PureComponent over Component?

The difference between a PureComponent and Component is that a PureComponent does a shallow comparison on both prop and state change and it handles the shouldComponentUpdate method for you. When comparing primitive values it compares their values, but when comparing objects it compares only references. It helps to improve the performance of the app.

You should use a PureComponent when you can satisfy any of the below conditions:

- State/Props should be an immutable object
- State/Props should not have a hierarchy
- You should call forceUpdate when data changes
- If you are using React.PureComponent you should make sure all child components are also pure.

---

### QUESTION 6) What is a higher order component?

Higher order components are JavaScript functions used for adding additional functionalities to the existing component. They are receiving data and returning values according to that data. If the data changes, higher order functions are re-run with different data input. If we want to update our returning component, we don't have to change the HOC. All we need to do is change the data that our function is using.

Higher Order Component (HOC) is wrapping around "normal" component and provide additional data input. It is actually a function that takes one component and returns another component that wraps the original one.

---

### QUESTION 7) Which (if there is) node library method could you use to solve the algorithm problem you solved last night in your pre-homework.

Authentication is the process of verifying the identity of the sender. Authentication algorithms use a shared key to verify the authenticity of the IPsec devices. Examples of authentication algorithms:

1. Message Digest 5 (MD5) uses a one-way hash function to convert a message of arbitrary length to a fixed-length message digest of 128 bits. Because of the
   conversion process, it is mathematically infeasible to calculate the original message by computing it backwards from the resulting message digest. Likewise,
   a change to a single character in the message will cause it to generate a very different message digest number.

2. Secure Hash Algorithm 1 (SHA-1) uses a stronger algorithm than MD5. SHA-1 takes a message of less than 264 bits in length and produces a 160-bit message
   digest. The large message digest ensures that the data has not been changed and that it originates from the correct source. SHA-256, SHA-384, and SHA-512 (sometimes grouped under the name SHA-2) are variants of SHA-1 and use longer message digests.

The Auth0 React SDK to secure React applications, which provides an easier way to add user authentication to React applications using a hooks-centric approach. The Auth0 React SDK provides a high-level API to handle a lot of authentication implementation details.

You first integrate your application with Auth0. Your application will then redirect users to an Auth0 customizable login page when they need to log in. Once your users log in successfully, Auth0 redirects them back to your app, returning JSON Web Tokens (JWTs) with their authentication and user information. With Auth0, you can secure a web application without having to know the ins and outs of identity protocols like OAuth 2.0 or OpenID Connect.

---

### QUESTION 8) Which (if there is) node library method could you use to solve the algorithm problem you solved in class tonight?

JavaScript doesn’t have a native Str#reverse method. Yet, you can use the existing methods to build your own method to reverse a string.

Creating the reverse string requires you to split an existing string into an array of its characters. JavaScript’s array class comes with a reverse method allowing you to reverse the order of the characters. Then you must join the items in the array back to a string value:

```
function reverse(str) {
 return Array.from(
String(str || '')
).reverse().join('')
}

reverse('Super')
// Expected output 'repuS'
```

There is a npm packages called @supercharge/strings that is a package that provides multiple string utilities. On of which is the Str#reverse(), that returns
a reversed string value.

```
const str = require ('@supercharge/strings)
Str('Super').reverse.get
// Expected output 'repuS'
```

---

### QUESTION 9) How do you think you might use the checkAuth() function to actually verify a user's email and password?

You can use the checkAuth() as a way to bring in the authentication to a frontend. Let's say there is an api called user/validate which is used to return
an authenticated flag, along with anything else such as a web token or information request. The checkAuth() will request this authentication.

A rough example would be:

```
const checkAuth = () => {
const url = "Some url"
someRequest(url, (res) => {
    if(res.status === 200 && res.data.isAuthenticated === true){
        cookie(some sort of cookie key, res.data.some sort of token)
        }
    })
}
```
