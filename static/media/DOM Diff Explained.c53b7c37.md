# DOM Diff

### Suppose that we have a virtual dom node:

(The following codes are written in Vue)

```html
<template>
  <div :class="x">
    <span v-if="y">{string1}</span>
    <span>{string2}</span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        x: "red",
        y: true,
        string1: "hello",
        string2: "world",
      };
    },
  };
</script>
```

![](/images/domdiff/1.png)

## When data mutates pt.1:

```html
<template>
  <div :class="x">
    <span v-if="y">{string1}</span>
    <span>{string2}</span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        x: "green",
        y: true,
        string1: "hello",
        string2: "world",
      };
    },
  };
</script>
```

![](/images/domdiff/2.png)

### DOM Diff finds that:

1. The div element's type stayed the same, only its property needs update, which in this case will be the class property
2. The children elements did not change, so no updates.

## When data mutates pt.2:

```html
<template>
  <div :class="x">
    <span v-if="y">{string1}</span>
    <span>{string2}</span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        x: "red",
        y: true,
        string1: "hello",
        string2: "world",
      };
    },
  };
</script>
```

![](/images/domdiff/1.png)

```html
<template>
  <div :class="x">
    <span v-if="y">{string1}</span>
    <span>{string2}</span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        x: "red",
        y: false,
        string1: "hello",
        string2: "world",
      };
    },
  };
</script>
```

![](/images/domdiff/3.png)

### DOM Diff finds that:

1. The div element stayed the same, no update.
2. first span element stayed the same, but its children changed, update the DOM.
3. second span element is removed, remove it from the DOM.

## Recap: What is DOM Diff anyway?

1. It is essentially a function, we call it patch.
2. patches = patch(oldVNode,newVNode)
3. patches will be the DOM operation that we will eventaully make. It might look like this:

```js
[
  {type: 'INSERT',vNode: ...},
  {type: 'TEXT', vNode:...},
  {type: 'PROPS', propsPatch: [...]}
]
```

## Potential DOM Diff logics:

- Tree diff

1.  Compare the old and new VNode trees, find out which nodes need to be updated.
2.  If the VNode is a component then -> Component diff
3.  If the VNode is a dom element then -> Element diff

- Component diff

1.  If VNode is a component then look at its component type
2.  If the types are different then replace the old VNode with the new one.
3.  If the types are the same then only update its properties.
4.  Then Tree diff this component(recursively)

- Element diff

1.  If VNode is a dom element then look at its tag name.
2.  If tag names are different then repalce the old tag with the new tag, if the same then only update its properties.
3.  Then Tree diff this element's children(recursively)

## Why is key needed when rendering an array of elements?

Check the Vue code [here](https://codesandbox.io/s/vue-template-z5xud?fontsize=14&file=/src/App.vue)

As you can see, the code gets rendered like this:

![](/images/domdiff/code1.png)

However, if I do:

![](/images/domdiff/code2.gif)

Suprised! We would expect that the second child gets deleted, but this is not the case!

So what happened? The reason is quite simple, as human being, you would think you have just deleted 2, but Vue would think that you:

1. changed 2 to 3
2. deleted 3

![](/images/domdiff/4.png)

![](/images/domdiff/5.png)

## Solution

### Use keys!!

Check the code right [here](https://codesandbox.io/s/vue-template-xmt14?fontsize=14)

You can see now this time we added a id field for each item, and pass it as the key to the v-for loop

![](/images/domdiff/code3.gif)

Everything works!

### Why?

The original array was:

```js
[
  { id: 1, value: 1 },
  { id: 2, value: 2 },
  { id: 3, value: 3 },
];
```

After clicking delete:

```js
[
  { id: 1, value: 1 },
  { id: 3, value: 3 },
];
```

When Vue compares them, it will find that the

1. The ids change from 1 2 3 to 1 3
2. Then it will compare the 1 in old array, the 1 in new array, 3 in old array, 3 in new array, nothing changed, so Vue would think 2 got deleted.

## Do not use index as the key!

Becuase if you use index as the key, you would likely run into the same problem I mentioned above.

## What if I don't have an ID?

1. Create a id() function, which returns a self-increment number.
2. Use guid or uuid library.
3. Use the id field in your database.
