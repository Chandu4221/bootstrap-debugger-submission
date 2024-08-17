### Helper Class to debug the `container`

Introduce a new CSS class `debugger`, to visually aid in understanding and troubleshooting Bootstrap grid layouts. By utilizing the `::after` pseudo-element, we can efficiently generate the grid overlay without introducing additional HTML elements, minimizing performance impact and maintaining code cleanliness. By quickly identifying and resolving grid-related issues, developers can significantly improve their efficiency and create more accurate layouts.

```html
<body class="container debugger">
  ....
</body>
```

```css
.debugger {
  --noOfGrids: 12;
  --gridSize: calc((100% / var(--noOfGrids) - var(--bs-gutter-x)));
  --gutterSize: calc(var(--bs-gutter-x) * 0.5);
  --gutterColor: var(--bs-primary-bg-subtle);
  --gridColor: var(--bs-primary);
  &::after {
    content: "";
    margin: auto;
    max-width: inherit;
    height: 100vh;
    position: fixed;
    z-index: -1;
    left: 0;
    right: 0;
    top: 0;
    background-image: repeating-linear-gradient(
      to right,
      var(--gutterColor) 0px,
      var(--gutterColor) var(--gutterSize),
      var(--gridColor) var(--gutterSize),
      var(--gridColor) calc(var(--gridSize) + var(--gutterSize)),
      var(--gutterColor) calc(var(--gridSize) + var(--gutterSize)),
      var(--gutterColor) calc(var(--gridSize) + (var(--gutterSize) * 2))
    );
  }
}
```
