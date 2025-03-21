## Disable all CSS styles on the page

```js
document.querySelectorAll('style, link[rel="stylesheet"]').forEach(e => e.remove());
```