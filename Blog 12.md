### QUESTION 1) Discuss in words something you learned in class today or this week.

This week we learned about Redux thunk, which is a functional programming technique used to delay computation. Instead of performing work now, you produce a function body (the 'thunk') which can optionally be used to perform the work later. In React / Redux, thunks enable us to avoid directly causing side effects in out actions, action creators, or components. Later, that thunk will be invoked by middleware to actually cause the effect. By transferring out side effects to running at a single point of the Redux loop(at the middleware level), the rest of the app stays relatively pure. Pure functions and components are easier to reason about, test, maintain, extend and reuse.

---

### QUESTION 2) What are “actions” in Redux?

Actions are a plain JavaScript object that contains information. Actions are the only source of information for the store. Actions have a type field that tells what kind of action to perform and all other fields contain information or data. And there is one other term called Action Creators, these are the function that creates actions. So actions are the information (Objects) and action creator are functions that return these actions.

---

### QUESTION 3) What is the role of reducers in Redux?

Reducers are a pure function in Redux and are the only way to change states in Redux. It is the only place where you can write logic and calculations. Reducer function will accept the previous state of app and action being dispatched, calculate the next state and returns the new object.

The following few things should never be performed inside the reducer:

1. Mutation of functions arguments
2. API calls & routing logic
3. Calling non-pure function e.g. Math.random()

---

### QUESTION 4) What is the meaning of “single source of truth” in Redux?

The global state of your application is stored in an object tree within a single store.

This makes it easy to create universal apps, as the state from your server can be serialized and hydrated into the client with no extra coding effort. A single state tree also makes it easier to debug or inspect an application; it also enables you to persist your app's state in development, for a faster development cycle. Some functionality which has been traditionally difficult to implement - Undo/Redo, for example - can suddenly become trivial to implement, if all of your state is stored in a single tree.

---

### QUESTION 5) Explain the working pieces of Redux.

Redux comprises of three parts:

1. The Store holds the state of the entire application. There can be only one Store per Application. As a developer, we can access, Update, register, or unregister the state in the store.

2. Actions are events. This is the place where we make all our requests to any API calls or User Interaction. Actions are sent using store.dispatch() function.

3. Reducers are pure functions that take the current state of an application, perform an action, and return a new state. These states are stored as objects, and they specify how the state of an application changes in response to an action sent to the store.

---

### QUESTION 6) Which (if there is) node library method could you use to solve the algorithm problem you solved in class today?

Problem: Check if a string (first argument, str) ends with the given target string (second argument, target).
This challenge can be solved with the .endsWith() method, which was introduced in ES2015. But for the purpose of this challenge, we would like you to use one of the JavaScript substring methods instead.

My first solution was primitive as I just tried to find a hardcoded value that would result in the appropriate responses to the function invocations. I used to the substr method to select the letter at the given index. In this case, it was the last letter in the string indicated by index of -1. If that letter was the same as the target, it would result in true, else it would be false.

```
const endsWith = (str, target) => {
  if(str.substr(-1) === target){
    return true
  } else return false
}

console.log(endsWith('Bastian', 'n')) // true
console.log(endsWith('Bastian', 'm')) // false
```

My second attempt was to try to find a dynamic approach to solve this. While still using the substr method, I determined that if target.length = 1, the opposite could be used to give me the -1 in the code above. By setting the target.length to -target.length, it would result in -1. Therefore, the -target.length could be used determine the number of letters selected in the string for comparison with the target.

```
const endsWith2  = (str, target) => {
  if(str.substr(-target.length) === target) {
    return true
  }else return false
}

console.log(endsWith2('Bastian', 'tian')) // true
console.log(endsWith2('Bastian', 'mian')) // false

```

---
