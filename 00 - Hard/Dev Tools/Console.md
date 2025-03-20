
## List all event listeners on the entire page


```js
$$("*").map(el => {
  return { el, listeners: getEventListeners(el) };
}).filter(data => {
  return Object.keys(data.listeners).length;
});

```

## Find all elements with a specific style
```js
var whatToFind = {
  property: "cursor",
  values: ["pointer"]
};

var walker = document.createTreeWalker(
  document.documentElement,
  NodeFilter.SHOW_ELEMENT,
  el => {
    const style = getComputedStyle(el)[whatToFind.property];
    return whatToFind.values.includes(style)
      ? NodeFilter.FILTER_ACCEPT
      : NodeFilter.FILTER_SKIP;
  }
);

while (walker.nextNode()) {
  console.log(walker.currentNode); 
}
```

## Monitor all events dispatched on an element
1. Select an element in the **Elements** panel.
2. Go to the **Console**.
3. Type `monitorEvents($0, 'key');` and hit Enter.
4. Interact with the selected element in the page to dispatch events.

```js
monitorEvents($0, 'key');
```

## Find DOM elements from the console

|                             | alt |
| --------------------------- | --- |
| document.querySelector()    | $   |
| document.querySelectorAll() | \$$ |

## Copy an object from the console

```js
copy($$('a').map(a => a.href).join('\n'))
```