### QUESTION 1) Discuss in words something you learned in class today or this week.

This week we learned about Redux. Redux is simply a store that stores the state of the variables in your app. It creates a process and procedures to interact with the store so that components will not just update or read the store randomly. Similar to the bank, it does not mean because you have money in the bank that you can go anytime, open the vault, and take money. You have to go through certain steps to withdrawal money.

Redux is a way to manage the state that can be accessed by all components with a structured way. It has to be accessed through a “Reducer” and “Actions”.

The store created will call the reducer and initialize the initial state. The reducer is a pure function that takes currentState and Action and returns a new state. A valid Reducer can return the current state. We have to create the Reducer before the store because it is needed for creating the store. The reducer is a function with a switch statement to decide which action to execute according to the action.type. Another method that we execute on the store is to dispatch an action.

---

### QUESTION 2) What is Redux?

Redux is a light weighted State Management Tool that helps the components in our React App to communicate with each other. The simple concept behind this is that every state of the component is kept in a store that will be global. So that every component can access any state from that store.

Redux application consists of a global store that will hold the state of the entire application. Each of the components can access the central store to access the state.

Redux comprises of three parts:

1. The Store holds the state of the entire application. There can be only one Store per Application. As a developer, we can access, Update, register, or unregister the state in the store.

2. Actions are events. This is the place where we make all our requests to any API calls or User Interaction. Actions are sent using store.dispatch() function.

3. Reducers are pure functions that take the current state of an application, perform an action, and return a new state. These states are stored as objects, and they specify how the state of an application changes in response to an action sent to the store.

Benefits to using Redux:

1. Access States Globally: One can easily manage the state of an application since the state is made global.

2. Easy Communication: Helps the components to communicate with each other easily without sending any props from one component to another.

3. Maintainability: Redux helps us to organize our codebase. So that someone with good knowledge of Redux can easily understand the structure of the Application.

4. Testing and Debugging: Redux helps us with Testing and Debugging a code easily.

---

### QUESTION 3) What is ‘Store’ in Redux?

A store is an immutable object tree in Redux. A store is a state container which holds the application's state. Redux can have only a single store in your application. Whenever a store is created in Redux, you need to specify the reducer.

A store is not a class. It's just an object with a few methods on it. To create it, pass your root reducing function to createStore.

---

### QUESTION 4) How is state changed in Redux?

The state can only be changed by emitting an action. The state tree is never mutated directly instead you use pure functions called reducers. A reducer takes the current state tree and an action as arguments and returns the resulting state tree.

Because we want the reducer to be a pure function, it is important that doesn’t mutate the state directly. So instead of pushing a new element to the array we create a brand new array containing all the previous state in addition to the new element.

---

### QUESTION 5) What is the difference between a Presentational component and a Container component?

Presentational components are mostly concerned with generating some markup to be outputted. They don’t manage any kind of state, except for state related to the presentation.

Container components are mostly concerned with the “backend” operations. They might handle the state of various sub-components. They might wrap several presentational components. They might interface with Redux.

As a way to simplify the distinction, we can say presentational components are concerned with the look, container components are concerned with making things work.

For example a component like this:

```
import React from "react";

class CommentList extends React.Component {
  constructor() {
    super();
    this.state = { comments: [] }
  }

  componentDidMount() {
    fetch("/my-comments.json")
      .then(res => res.json())
      .then(comments => this.setState({ comments }))
  }

  render() {
    return (
      <ul>
        {this.state.comments.map(({ body, author }) =>
          <li>{body}-{author}</li>
        )}
      </ul>
    );
  }
}
```

It could be split into two components. The first is like a presentation component, only concerned with presentation, and the second is tasked with fetching data and rendering the related view component.

```
// CommentList.js
import React from "react";

const Commentlist = comments => (
  <ul>
    {comments.map(({ body, author }) =>
      <li>{body}-{author}</li>
    )}
  </ul>
)
```

```
// CommentListContainer.js
import React from "react";
import CommentList from "./CommentList";

class CommentListContainer extends React.Component {
  constructor() {
    super();
    this.state = { comments: [] }
  }

  componentDidMount() {
    fetch("/my-comments.json")
      .then(res => res.json())
      .then(comments => this.setState({ comments }))
  }

  render() {
    return <CommentList comments={this.state.comments} />;
  }
}
```

Additionally, a Higher-order Component or component with Render Props could help in making container components and stateless components more composeable.

---

### QUESTION 6) What is the second argument that can optionally be passed to setState and what is its purpose?

When passing in an anonymous arrow function as the optional second parameter, it gets called immediately after setState finishes setting the new state.

Functions in code can depend on a state and render with a previous state instead of using an updated one. The reason for this is because setState is asynchronous. For example, if you were trying to console.log() a state before and after it had changed, it would end up logging the previous state.

When the anonymous function gets called immediately after setState finishes setting the new state, it solves the problem of setState being asynchronous. This allows us to perform actions immediately after a state change and be ensured that whatever data we render will utilize the newest state.

---

### QUESTION 7) Which (if there is) node library method could you use to solve the algorithm problem you solved last night in your pre-homework.

Bucket Sort is a sorting algorithm that separates elements into multiple groups called buckets, then they are sorted by any other sorting algorithm. Once sorted, the elements are gathered in a sorted manner.

Basic Steps:

1. Partition the range into a fixed number of buckets.
2. Toss every element into its appropriate bucket
3. Sort each bucket individually by applying a sorting algorithm.
4. Concatenate all the sorted buckets.

For example, say we have a range from 0-20 with values of: 12,19,7,1,6,16,4,11. We then could have four buckets with ranges 0-5,5-10,10-15,15-20. We can place the elements in their corresponding buckets as seen below:

| 0-5 | 5-10 | 10-15 | 15-20 |
| --- | ---- | ----- | ----- |
| 1,4 | 7,6  | 12,11 | 19,16 |

Then, they are sorted using a sorting algorithm of choice in their respective buckets:

| 0-5 | 5-10 | 10-15  | 15-20 |
| --- | ---- | ------ | ----- |
| 1,4 | 6,7  | 11, 12 | 16,19 |

Finally the buckets are concatenated together to get a sorted output of: 1,4,6,7,10.16,19

Node-Sort-Algorithms is an npm package that will perform various types of sorting, which include bucket sort. Its reference is:

```
var nodesort = require('./node-sort-algorithms');
var displaymode = "No";
...
nodesort(inputArray, displaymode, function(err,sortRef) {
        if (err) {
            // TODO error handling
            }
          else {
           var result = sortRef.beadSort(inputArray);
           // TODO output
                }
    });

```

---

### QUESTION 8) Which (if there is) node library method could you use to solve the algorithm problem you solved in class tonight?

The Counting Sort algorithm works by determining the positions of each key value in the output sequence by counting the number of objects with distinct key values and applying prefix sum to those counts. Because the life cycle runs proportionally to the number and the difference between the max and min key values, it is best suited for when the number of items is not much more than the variation in keys.

Let's say the array given is as follows:
| 8 | 3 | 5 | 1 | 8 | 3 | 5 | 1 | 1 |
| - | - | - | - | - | - | - | - | - |

First, you would find the largest element in the array and set it to the max. In this case it would be: 8

Next, to store the sorted date, initialize a new count array with length (max +1: 8 + 1 = 9) and all the elements set to 0.

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |

Now, store the elements of the array with corresponding index in the count array.

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   | 0   | 3   | 1   | 1   | 1   | 0   | 2   | 0   |

Next, you will change the count array by adding the previous counts to produce the cumulative sum of the array.

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   | 1   | 4   | 5   | 6   | 7   | 7   | 9   | 9   |

Because the original array has nine inputs, you will create another empty array with nine places to store the sorted data, place the elements in their correct positions, and reduce the count by one.

As a result, the sorted array is:

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 3   | 3   | 3   | 4   | 5   | 6   | 8   | 8   |

Same as above, Node-Sort-Algorithms is an npm package that will perform various types of sorting, which include count sort. Its reference is:

```
var nodesort = require('./node-sort-algorithms');
var displaymode = "No";
...
nodesort(inputArray, displaymode, function(err,sortRef) {
        if (err) {
            // TODO error handling
            }
          else {
           var result = sortRef.countSort(inputArray);
           // TODO output
                }
    });

```

---

### QUESTION 9) What is your opinion of currently popular frameworks/libraries? List and provide your thoughts.

I feel that frameworks like React and Express are extremely beneficial. Frameworks are sometimes necessary for working with complicated programming languages as they can provide understandable and integrable functions. Working with JavaScript, for example, would require writing huge lines of code for maintaining data consistency throughout the app. But frameworks like React do this automatically.

Similarly, they can automate a lot of other tasks by providing built-in functions that would be complicated for us. All major languages have multiple frameworks for different usage needs. They also are a great way to explore and learn a new language. Just understanding the basic programming concepts of the language, you can start coding in the framework.

Also, the greatly enhance development process. You can develop custom applications within a short time, building up ready-made templates according to one’s needs. They also provide great flexibility to developers for experimenting and implementing creative solutions.

Another advantage is that they provide reusability. The building of reusable components that can be integrated into other areas of the code and even in different projects.
