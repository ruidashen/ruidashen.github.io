## Event delegation

Event delegation in plain english means to delegate a event handler function from an element to another element.
Generally speaking, we often delegate one or a group of elements's event handler to their parent element, when an event is triggered, it will bubble up to the element that acutually binds the event handler function.

**Advantages of event delegation:**

- Reduce memory consumption

Imagine if we have a list with a large number of list items, and we need to respond to an event when we click on the list item.

```html
<ul id="list">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
  ......
  <li>item n</li>
</ul>
```

If you bind a function to each list item one by one, it is very memory intensive and requires a lot of performance in terms of efficiency.

Therefore, a better approach would be to bind this click event to its parent, `ul`, and then match to determine the target element when the event is executed.

So event delegation can reduce significant memory consumption and save efficiency.

- Binding events dynamically

For example, in the above example there are just a few list items and we bind events to each list item.

In many cases, we need to dynamically add or remove list item elements via AJAX or user actions, so we need to re-bind events to the new elements and unbind events to the elements to be deleted each time we change them.

There is no such trouble if event delegation is used, because events are bound to the parent level and have no relation to the increase or decrease of the target element.

Using event delegation can reduce a lot of duplicate work.

**Implementation**

```js
function delegate(element, eventType, selector, fn) {
  element.addEventListener(eventType, (e) => {
    let el = e.target;
    while (!el.matches(selector)) {
      if (element === el) {
        el = null;
        break;
      }
      el = el.parentNode;
    }
    el && fn.call(el, e, el);
  });
  return element;
}
```
