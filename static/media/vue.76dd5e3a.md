## Vue interview questions notes

### 1. Computed vs. Watch

### A:

A computed value is cached, only if it's dependencies change so then it will recalculate the value, however a watched function will be invoked everytime the value it watches change.

### 2. What are some life cycle methods?

### A:

oncreated, onmounted,onupdated,ondestroyed, .etc..

### 3. How do components communicate with each other?

### A:

- Child-Parent: using custom event, e.g. $emit("event",data), $on("event",(data)=>{})
- Siblings: use event bus
  grandparent-child: custom event, use $emit and $on two times
- other: Vuex

### 4. How do you use Vuex?

### A:

Vuex is a centralized state management library built for Vue.
There are 5 key concepts about Vuex:

1. state: a single object that contains all your application state.
2. getters: getters function are like computed properties for stores, for example, your state contains an array of todo list items, you can define a doneTodos getter function to get all the items that are done, this way you don't have to write a seperate function to
   do the same thing.
3. mutations: a mutation is the only way to change state in a Vuex store, mutations must be synchronous, for debugging and other reasons.
4. Actions are similar to mutations, the differences being that:

   - Instead of mutating the state, actions commit mutations.
   - Actions can contain arbitrary asynchronous operations.

5. Modules: A store can be divided into modules. Each module can contain its own state, mutations, actions, getters, and even nested modules

### 5. How does Vue.js reactivity work?

### A:

In Vue2.x,When you pass a plain JavaScript object to a Vue instance as its data option, Vue will walk through all of its properties and convert them to getter/setters using `Object.defineProperty`.
In Vue3.x, this is achived by Proxy, this fixs the problem where Vue cannot detech the addition or deletion of an object property, to solve this we used to use `Vue.set` or `this.$set`.

### 6. What is Vue Router?

### A:

Vue Router is the offcial router for Vue.js.
common apis: `<router-link>` `<router-view>` `<this.$router.push>` `<this.$router.replace>` `<this.$router.params>`

### 6. What are navigation guards?

### A:

A set of actions we can do before leaving/entering an url.
