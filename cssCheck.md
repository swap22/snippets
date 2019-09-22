# CSS 

### flex layout

basic concepts:

<img src="https://www.runoob.com/wp-content/uploads/2015/07/3791e575c48b3698be6a94ae1dbff79d.png" />

- 🔥flex-direction (determines the direction of the main axis): row | row-reverse | column | column-reverse;
  - row (default): The spindle is horizontal and the starting point is at the left.
  - row-reverse: The main axis is horizontal and the starting point is at the right end.
  - column: The main axis is in the vertical direction and the starting point is in the upper edge.
  - column-reverse: the main axis is vertical and the starting point is at the bottom
- 🔥justify-content (the alignment of the project on the spindle): flex-start | flex-end | center | space-between | space-around;
  - flex-start (default): left aligned
  - flex-end: right alignment
  - center: centered
  - space-between: Justified, the intervals between items are equal.
  - space-around: The spacing between the sides of each item is equal. Therefore, the interval between projects is twice as large as the interval between the project and the border.
- 🔥 align-items (how the item is aligned on the cross axis): flex-start | flex-end | center |
  - flex-start: The starting point of the cross axis is aligned.
  - flex-end: The end of the cross axis is aligned.
  - center: Midpoint alignment of the intersecting axes.
  - baseline: Baseline alignment of the first line of text in the project.
  - stretch (default): if the item is not set to height or set to auto, it will fill the height of the entire container
- [More access] (https://www.runoob.com/w3cnote/flex-grammar.html)

## Basic CSS 
###  Clear floating (float)

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}
.floated {
  float: left;
}
```

---

###  The child box expands the parent box, so that the height of the parent box is adaptive with the content.

```css
height: auto
```

---

###  Center the element vertically to another element

```html
<div class="ghost-trick">
  <div class="ghosting"><p>Vertically centered without changing the position property.</p></div>
</div>
```

```css
.ghosting {
  height: 300px;
  background: #0ff;
}
.ghosting:before {
  content: '';
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}
p {
  display: inline-block;
  vertical-align: middle;
}
```


---

###  Constant aspect ratio

```html
<div class="constant-width-to-height-ratio"></div>
```

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

---

##  Common styles

### 1. Reset style

**reset.css**

```css
/* http://meyerweb.com/eric/tools/css/reset/
   V2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
margin: 0;
padding: 0;
border: 0;
font-size: 100%;
font: inherit;
vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
display: block;
}
body {
line-height: 1;
}
ol, ul {
list-style: none;
}
blockquote, q {
quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
content: '';
content: none;
}
table {
border-collapse: collapse;
border-spacing: 0;
}
```

---

**normalize.css**

[The content is too much to copy, check this paste] (https://necolas.github.io/normalize.css/latest/normalize.css)

### 2.Create a loading animation

**Load animation one**

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

```css
@keyframes bouncing-loader {
  To {
    Opacity: 0.1;
    Transform: translate3d(0, -1rem, 0);
  }
}
.bouncing-loader {
  Display: flex;
  Justify-content: center;
}
.bouncing-loader > div {
  Width: 1rem;
  Height: 1rem;
  Margin: 3rem 0.2rem;
  Background: #8385aa;
  Border-radius: 50%;
  Animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  Animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  Animation-delay: 0.4s;
}
```


---

**Load animation two**

```html
<div class="donut"></div>
```

```css
@keyframes donut-spin {
  0% {
    Transform: rotate(0deg);
  }
  100% {
    Transform: rotate(360deg);
  }
}
.donut {
  Display: inline-block;
  Border: 4px solid rgba(0, 0, 0, 0.1);
  Border-left-color: #7983ff;
  Border-radius: 50%;
  Width: 30px;
  Height: 30px;
  Animation: donut-spin 1.2s linear infinite;
}
```
---

### 3. Button border animation

```html
<div class="button-border"><button class="button">Submit</button></div>
```

```css
.button {
  Background-color: #c47135;
  Border: none;
  Color: #ffffff;
  Outline: none;
  Padding: 12px 40px 10px;
  Position: relative;
}
.button:before,
.button:after {
  Border: 0 solid transparent;
  Transition: all 0.25s;
  Content: '';
  Height: 24px;
  Position: absolute;
  Width: 24px;
}
.button:before {
  Border-top: 2px solid #c47135;
  Left: 0px;
  Top: -5px;
}
.button:after {
  Border-bottom: 2px solid #c47135;
  Bottom: -5px;
  Right: 0px;
}
.button:hover {
  Background-color: #c47135;
}
.button:hover:before,
.button:hover:after {
  Height: 100%;
  Width: 100%;
}
```


---

### 4.Create graphics using CSS

**Circle**

```html
<div class="circle"></div>
```

```css
.circle {
  Border-radius: 50%;
  Width: 2rem;
  Height: 2rem;
  Background: #333;
}
```


---

**triangle**

```html
<div class="triangle"></div>
```

```css
.triangle {
  Width: 0;
  Height: 0;
  Border-top: 20px solid #333;
  Border-left: 20px solid transparent;
  Border-right: 20px solid transparent;
}
```
---

### 5.li tag counter

```html
<ul>
  <li>List item</li>
  <li>List item</li>
  <li>
    List item
    <ul>
      <li>List item</li>
      <li>List item</li>
      <li>List item</li>
    </ul>
  </li>
</ul>
```
```css
Ul {
  Counter-reset: counter;
}
Li::before {
  Counter-increment: counter;
  Content: counters(counter, '.') ' ';
}
```

---

### 6. Custom scroll bar

```html
<div class="custom-scrollbar">
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit.<br />
    Iure id exercitationem nulla qui repellat laborum vitae, <br />
    Molestias tempora velit natus. Quas, assumenda nisi. <br />
    Quisquam enim qui iure, consequatur velit sit?
  </p>
</div>
```
```css
.custom-scrollbar {
  Height: 70px;
  Overflow-y: scroll;
}
/* To style the document scrollbar, remove `.custom-scrollbar` */
.custom-scrollbar::-webkit-scrollbar {
  Width: 8px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  Box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  Border-radius: 10px;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  Border-radius: 10px;
  Box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
```
---

### 7. Custom text selection effect

```html
<p class="custom-text-selection">Select some of this text.</p>
```

```css
::selection {
  Background: aquamarine;
  Color: black;
}
.custom-text-selection::selection {
  Background: deeppink;
  Color: white;
}
```
---

### 8. Make text content cannot be selected

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

```css
.unselectable {
  User-select: none;
}
```

---

### 9. Custom variables

```html
<p class="custom-variables">CSS is awesome!</p>
```

```css
:root {
  /* Place variables here to use variables globally. */
}
.custom-variables {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
  Color: var(--some-color);
  Font-size: var(--some-size);
  Font-style: var(--some-keyword);
  Text-shadow: var(--some-complex-value);
}
```
---

### 10. Dynamic shadow (shadow based on the color of the element itself)

```html
<div class="dynamic-shadow"></div>
```

```css
.dynamic-shadow {
  Position: relative;
  Width: 10rem;
  Height: 10rem;
  Background: linear-gradient(75deg, #6d78ff, #00ffb8);
  Z-index: 1;
}
.dynamic-shadow::after {
  Content: '';
  Width: 100%;
  Height: 100%;
  Position: absolute;
  Background: inherit;
  Top: 0.5rem;
  Filter: blur(0.4rem);
  Opacity: 0.7;
  Z-index: -1;
}
```

---

### 11. Appropriate display image in the container

Change the fit and position of an image within its container while preserving its aspect ratio. Previously only the background image and the background-size attribute could be used.

```html
<img class="image image-contain" src="https://picsum.photos/600/200" />
<img class="image image-cover" src="https://picsum.photos/600/200" />
```

```css
.image {
  Background: #34495e;
  Border: 1px solid #34495e;
  Width: 200px;
  Height: 200px;
}
.image-contain {
  Object-fit:'';
  Object-position: center;
}
.image-cover {
  Object-fit: cover;
  Object-position: right top;
}
```

---

### 12. Gradient text

```html
<p class="gradient-text">Gradient text</p>
```

```css
.gradient-text {
  Background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```

---

### 13. Hover effect animation

**Hovering shadow box animation**

```html
<p class="hover-shadow-box-animation">Box it!</p>
```

```css
.hover-shadow-box-animation {
  Display: inline-block;
  Vertical-align: middle;
  Transform: perspective(1px) translateZ(0);
  Box-shadow: 0 0 1px transparent;
  Margin: 10px;
  Transition-duration: 0.3s;
  Transition-property: box-shadow, transform;
}
.hover-shadow-box-animation:hover,
.hover-shadow-box-animation:focus,
.hover-shadow-box-animation:active {
  Box-shadow: 1px 10px 10px -10px rgba(0, 0, 24, 0.5);
  Transform: scale(1.2);
}
```
**Hovering underline animation**

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

```css
.hover-underline-animation {
  Display: inline-block;
  Position: relative;
  Color: #0087ca;
}
.hover-underline-animation::after {
  Content: '';
  Position: absolute;
  Width: 100%;
  Transform: scaleX(0);
  Height: 2px;
  Bottom: 0;
  Left: 0;
  Background-color: #0087ca;
  Transform-origin: bottom right;
  Transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  Transform: scaleX(1);
  Transform-origin: bottom left;
}
```

**Mouse cursor gradient tracking**

```html
<button class="mouse-cursor-gradient-tracking"><span>Hover me</span></button>
```

```css
.mouse-cursor-gradient-tracking {
  Position: relative;
  Background: #7983ff;
  Padding: 0.5rem 1rem;
  Font-size: 1.2rem;
  Border: none;
  Color: white;
  Cursor: pointer;
  Outline: none;
  Overflow: hidden;
}
.mouse-cursor-gradient-tracking span {
  Position: relative;
}
.mouse-cursor-gradient-tracking::before {
  --size: 0;
  Content: '';
  Position: absolute;
  Left: var(--x);
  Top: var(--y);
  Width: var(--size);
  Height: var(--size);
  Background: radial-gradient(circle closest-side, pink, transparent);
  Transform: translate(-50%, -50%);
  Transition: width 0.2s ease, height 0.2s ease;
}
.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

```js
Var btn = document.querySelector('.mouse-cursor-gradient-tracking')
Btn.onmousemove = function(e) {
  Var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
  Var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```
---

### 14.:not create elements

```html
<ul class="css-not-selector-shortcut">
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
  <li>Four</li>
</ul>
```

```css
.css-not-selector-shortcut {
  Display: flex;
}
Ul {
  Padding-left: 0;
}
Li {
  List-style-type: none;
  Margin: 0;
  Padding: 0 0.75rem;
}
Li:not(:last-child) {
  Border-right: 2px solid #d2d5e4;
}
```
---

### 15. Overflow scrolling gradient

```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. <br />
    Iure id exercitationem nulla qui repellat laborum vitae, <br />
    Molestias tempora velit natus. Quas, assumenda nisi. <br />
    Quisquam enim qui iure, consequatur velit sit? <br />
    Lorem ipsum dolor sit amet consectetur adipisicing elit.<br />
    Iure id exercitationem nulla qui repellat laborum vitae, <br />
    Molestias tempora velit natus. Quas, assumenda nisi. <br />
    Quisquam enim qui iure, consequatur velit sit?
  </div>
</div>
```

```css
.overflow-scroll-gradient {
  Position: relative;
}
.overflow-scroll-gradient::after {
  Content: '';
  Position: absolute;
  Bottom: 0;
  Width: 240px;
  Height: 25px;
  Background: linear-gradient(
    Rgba(255, 255, 255, 0.001),
    White
  ); /* transparent keyword is broken in Safari */
  Pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  Overflow-y: scroll;
  Background: white;
  Width: 240px;
  Height: 200px;
  Padding: 15px;
  Line-height: 1.2;
}
```

---

### 16. Beautiful text emphasizes

A better alternative to text-decoration: underline or <u></u> descenders won't cut underscores. Native implementation, text-decoration-skip-ink: auto but it has less control over underscores.

```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```

```css
.pretty-text-underline {
  Display: inline;
  Text-shadow: 1px 1px #f5f6f9, -1px 1px #f5f6f9, -1px -1px #f5f6f9, 1px -1px #f5f6f9;
  Background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  Background-position: bottom;
  Background-repeat: no-repeat;
  Background-size: 100% 1px;
}
.pretty-text-underline::-moz-selection {
  Background-color: rgba(0, 150, 255, 0.3);
  Text-shadow: none;
}
.pretty-text-underline::selection {
  Background-color: rgba(0, 150, 255, 0.3);
  Text-shadow: none;
}
```

---

### 17. Split line

**Graphic dividing line**

```html
<div class="shape-separator"></div>
```

```css
.shape-separator {
  Position: relative;
  Height: 48px;
  Background: #333;
}
.shape-separator::after {
  Content: '';
  Background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 12'%3E%3Cpath d='m12 0l12 12h-24z' fill='%23fff'/%3E%3C/svg%3E");
  Position: absolute;
  Width: 100%;
  Height: 12px;
  Bottom: 0;
}
```

---

**Envelope dividing line**

```js
<hr style="content: '';
    Left: 0;
    Right: 0;
    Bottom: 0;
    Background: repeating-linear-gradient(-45deg, #ff6c6c 0, #ff6c6c 20%, transparent 0, transparent 25%, #1989fa 0, #1989fa 45%, transparent 0, transparent 50%);
    Height: 2px;
    Background-size: 80px;" />
```

**Show results**

<hr style="content: '';
    Left: 0;
    Right: 0;
    Bottom: 0;
    Background: repeating-linear-gradient(-45deg, #ff6c6c 0, #ff6c6c 20%, transparent 0, transparent 25%, #1989fa 0, #1989fa 45%, transparent 0, transparent 50%);
    Height: 2px;
    Background-size: 80px;" />

---

### 18. Fading unselected items

```html
<div class="sibling-fade">
  <span>Item 1</span> <span>Item 2</span> <span>Item 3</span> <span>Item 4</span>
  <span>Item 5</span> <span>Item 6</span>
</div>
```

```css
Span {
  Padding: 0 1rem;
  Transition: opacity 0.2s;
}
.sibling-fade:hover span:not(:hover) {
  Opacity: 0.5;
}
```

---
### 19. Using the native font of the operating system

```html
<p class="system-font-stack">This text uses the system font.</p>
```

```css
.system-font-stack {
  Font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```

### 20.CSS creates a switch

```html
<input type="checkbox" id="toggle" class="offscreen" /> <label for="toggle" class="switch"></label>
```

```css
.switch {
  Position: relative;
  Display: inline-block;
  Width: 40px;
  Height: 20px;
  Background-color: rgba(0, 0, 0, 0.25);
  Border-radius: 20px;
  Transition: all 0.3s;
}
.switch::after {
  Content: '';
  Position: absolute;
  Width: 18px;
  Height: 18px;
  Border-radius: 18px;
  Background-color: white;
  Top: 1px;
  Left: 1px;
  Transition: all 0.3s;
}
Input[type='checkbox']:checked + .switch::after {
  Transform: translateX(20px);
}
Input[type='checkbox']:checked + .switch {
  Background-color: #7983ff;
}
.offscreen {
  Position: absolute;
  Left: -9999px;
}
```

### 21. Truncating text

**End with an ellipsis**

```html
<p class="truncate-text">If I exceed one line's width, I will be truncated.</p>
```

```css
.truncate-text {
  Overflow: hidden;
  White-space: nowrap;
  Text-overflow: ellipsis;
  Width: 200px;
}
```


**Fade end **

```html
<p class="truncate-text-multiline">
  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut
  Labore et.
</p>
```

```css
.truncate-text-multiline {
  Overflow: hidden;
  Display: block;
  Height: 109.2px;
  Margin: 0 auto;
  Font-size: 26px;
  Line-height: 1.4;
  Width: 400px;
  Position: relative;
}
.truncate-text-multiline:after {
  Content: '';
  Position: absolute;
  Bottom: 0;
  Right: 0;
  Width: 150px;
  Height: 36.4px;
  Background: linear-gradient(to right, rgba(0, 0, 0, 0), #f5f6f9 50%);
}
```

---

### 22. Zebra Stripe List

```html
<ul>
  <li>Item 01</li>
  <li>Item 02</li>
  <li>Item 03</li>
  <li>Item 04</li>
  <li>Item 05</li>
</ul>
```

```css
Li:nth-child(odd) {
  Background-color: #eee;
}
```

