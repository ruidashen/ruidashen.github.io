## css Fundamentals

### Q: Content-box VS Border-box

### A:

In a content-box, the width = content width, e.g.:

```css
content-box {
  width: 100px;
  height: 100px;
  border: 50px solid;
  padding: 50px;
}
```

Then the box will look like:

![](/images/css1.png)

The actual width of this box is:
(50px _ 2)(border) + (50px _ 2)(padding) + 100px(content) = 300px

In a border-box, the width = content width + padding + border, e.g.

```css
border-box {
  width: 100px;
  height: 100px;
  border: 50px solid;
  padding: 50px;
}
```

![](/images/css2.png)

The actual width of this box is:
100px, however, because the border + padding is already 100px, the content width will shrink down to 0px, the box cannot hold any content.

### Q: What is A BFC?

### A:

A block formatting context is a part of a visual css rendering of a web page. It's the region in which the layout of block boxes occurs and in which floats interact with other elements (MDN).

A block formatting context is created by at least one of the following:

- Floats (elements where float isn't none).
- Absolutely positioned elements (elements where position is absolute or fixed).
- Inline-blocks (elements with display: inline-block).
- Block elements where overflow has a value other than visible.
- Flex items (direct children of the element with display: flex or inline-flex) if they are neither flex nor grid nor table containers themselves.

### Q: css specificity

### A:

The following list of selector types increases by specificity:

- Type selectors (e.g., h1) and pseudo-elements (e.g., ::before).
- Class selectors (e.g., .example), attributes selectors (e.g., `[type="radio"]`) and pseudo-classes (e.g., :hover).
- ID selectors (e.g., #example).

Inline styles added to an element (e.g., style="font-weight: bold;") always overwrite any styles in external stylesheets, and thus can be thought of as having the highest specificity.
