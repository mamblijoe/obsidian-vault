
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

## Download all images from the page

```js
$$('img').forEach(async (img) => {
  try {
    const src = img.src;

    // Fetch the image as a blob.
    const fetchResponse = await fetch(src);
    const blob = await fetchResponse.blob();
    const mimeType = blob.type;

    // Figure out a name for it from the src and the mime-type.
    const start = src.lastIndexOf('/') + 1;
    const end = src.indexOf('.', start);
    let name = src.substring(start, end === -1 ? undefined : end);
    name = name.replace(/[^a-zA-Z0-9]+/g, '-');
    name += '.' + mimeType.substring(mimeType.lastIndexOf('/') + 1);

    // Download the blob using a <a> element.
    const a = document.createElement('a');
    a.setAttribute('href', URL.createObjectURL(blob));
    a.setAttribute('download', name);
    a.click();
  } catch (e) {}
});
```

## Disable all CSS styles on the page

```js
document.querySelectorAll('style, link[rel="stylesheet"]').forEach(e => e.remove());
```