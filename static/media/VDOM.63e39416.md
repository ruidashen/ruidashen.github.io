# Virtual DOM Vs. DOM

## Adavantages of Virtual DOM:

### Under certain circumstances, Virtual DOM is faster than DOM:

1. Virtual DOM reduces DOM operations, In other words, virtual DOM batches DOM operations. For instance, if you want to add 1000 divs to the web page, without React or Vue, you need to add those divs one by one, which causes a lot of performance overhead. However, with React and Vue or other frame works that use Virtual DOM, you can put the divs inside an array, then the framework will take care of the rest, it might just take 1 DOM operation to finish the whole process!

2. Virtual DOM can get rid of unnecessary operations with the help of DOM Diff algorithms. With the same example above, if you want to add another 10 divs to the old page which contains 1000 divs, without Virtual DOM, the browser will just render the 1010 divs completely, however with Virtual DOM and DOM Diff, it knows that only the 10 divs are new, instead of rendering them all over again, they will be inserted into the DOM, therefore increase the performance.

### Virtual DOM is cross-platform:

1. Virtual DOM can not only turn into DOM(browser app), but can also turn into IOS and Android Apps(native apps), because Virtual DOM is essentially a JS object.

## What does Virtual DOM look like?

### React

```js
const vNode = {
  key: null,
  props: {
  children: [ // children elements
    { type: 'span',...},
    { type: 'span',...}
  ],
  className: "red" // element attribute
	onClick: ()=>{} // event handler
  },
  ref: null,
  type: 'div' // element name or component name
}

```

### Vue

```js
const vNode = {
  tag: 'div' // element name or component name,
  data: {
    class: "red" // element attribute
    on: {
      click: ()=>{} // event handler
    }
  },
  children: [ // children elements
    { type: 'span',...},
    { type: 'span',...}
  ],
}

```

## How to create Virtual DOM nodes:

### React

```js
// React.createElement
createElement("div", { className: "red", onClick: () => {} }, [
  createElement("span", {}, "span1"),
  createElement("span", {}, "span1"),
]);
```

```js
// JSX
<div className="red" onClick="{()=>{}}">
  <span>span1</span>
  <span>span2</span>
</div>
```

We can use Babel to transpile JSX to JavaScript.

### Vue

```js
// Vue(can only access the 'h' method inside render())
h(
  "div",
  {
    class: "red",
    on: {
      click: () => {},
    },
  },
  [h("span", {}, "span1"), h("span", {}, "span2")]
);
```

```js
// Vue template
<div class="red" @click="fn">
  <span>span1</span>
  <span>span1</span>
</div>

```

We can use vue-loader to transpile Vue template to JavaScript

## Conclusion

### - What is Virtual DOM?

- An object that represents the DOM tree, usually contains the element's name,
  attributes asscoiate with the element, event listeners and child elements, etc..

- Adavantages of the Virtual DOM

  - Reduce unnecessary DOM operations
  - Cross-platform rendering.

### - Disadvantages of the Virtual DOM

- Need extra methods to create Virtual DOM, such as createELement and h,
  however this can be simplified by using JSX
- Strongly rely on transpliers such as Babel and vue-loader
