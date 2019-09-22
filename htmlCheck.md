# 1.HTML and HTML5

### 1. Basic concepts

**Basic concept**

- Inline elements: Side by side with other inline elements, width and height cannot be set, the default width is the width of the text
- Block-level elements: Exclusive on one line, cannot be juxtaposed with any other element. Can accept the width and height, if you do not set the width, then the width will default to 100% of the parent
- Inline block elements: can be set width and height, alongside other elements
- Convert to each other: display:inline(block block level | inline-block inline block)

**Common label type**

- Inline elements: a, span, textarea, select, input, b, br...
- Block level elements: div, h1~h6, ol, ul, p, hr, form, table ...
- Inline block element: img...

---

### 2.HTML4.1 Common Tags

```html

<!-- div, span, h1~h6, p, hr, etc. Labels are not displayed -->

<!-- img tag can set a lot of properties -->
<img src="image address" title="text displayed when the text is hovering" alt="image failed to load, displayed replacement text" width="width" height="height" ...>

<a href="jump address" target="target window popup">text or image</a>
<!-- target: self is the default value, blank is open in a new window -->

<!-- Anchor Positioning -->
<!--  Set anchor point for a #idName -->
<a href="#test">Go to the target anchor</a>
<!-- Set the target anchor point -->
<h3 id="test">target anchor point</h3>

<!-- Form -->
<table>
    <caption>I am the table title</caption>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
            <th>Header 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>First line 1</td>
            <td>First line 2</td>
            <td>First line 3</td>
        </tr>
        <tr>
            <td>Second line 1</td>
            <td>Second line 2</td>
            <td>Second line 3</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">Remarks:</td>
        </tr>
    </tfoot>
</table>

<!-- list (and there are ordered lists and custom lists) -->
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>
        <div>4</div>
    </li>
</ul>

<!-- Form -->
<form action="Submitted to the url address" method="Submit method (value is get & post)" name="form name">
    <!-- input -->
    Account number: <input type="text" value="Please enter the account number" name="username" />
    Password: <input type="password" name="password" />

    <!-- achieve the radio effect by the same name -->
    <!-- Remarks: checked means the default is selected, often used for single-selection, multi-select scenes -->
    Gender: Male <input type="radio" name="sex" checked /> | Female <input type="radio" name="sex" />

    <!-- Multiple selection is also achieved by name -->
    Hobbies: Cricket <input type="checkbox" name="like" /> |  Basketball <input type="checkbox" name="like" /> | swimming <input type="checkbox" name="like " />

    <!-- Button Group: Submit & Reset All need to be in the form field to take effect. The default value is Submit and Reset -->
    <input type="submit" />
    <input type="reset" />
    <input type="button" value="a pure button" />

    <!-- Other: Image submission must include src attribute -->
    <input type="image" src="" />
    <input type="file" />

    <label>
        Account number: <input type="text" value="Please enter the account number" name="username" />
    </label>

    <textarea cols="Number of characters in each line" rows="Number of lines displayed">
        Text content
    </textarea>

    <select>
        <!-- selected indicates the default selected -->
        <option selected>--Please select the province--</option>
        <option>Delhi</option>
        <option>Mumbai</option>
        <option>Pune</option>
    </select>
</form>

<b>Bold display</b>
<strong>Bold display</strong>
<i>Italic display</i>
<em>Italic Display</em>
<s>Delete line display</s>
<del>Delete line display</del>
<u>underlined</u>
<ins>underlined</ins>


```

---

###  Canvas

### 1.canvas basic operation

```js
let canvas = document.getElementById('can')
let ctx = canvas.getContext('2d') // This can be understood as a brush

// line (straight line, triangle...)
ctx.moveTo(x, y)
ctx.lineTo(x, y)
ctx.arcTo(B point x, By, C point x, C point y, the value of the arc) // Line + Arc (can be rounded rectangle)

// rectangle
ctx.rect(x, y, width, height) // draw rectangle
ctx.strokeRect(x, y, width, height) // draw directly, no need to write the build path
ctx.fillRect(x, y, width, height) // draw directly, no need to write the fill path

// round (semicircle, fan, arc, circle)
ctx.arc (center x, center y, radius, radians, direction)

// Bezier curve
ctx.quadraticCurveTo(x1, y1, x2, y2); // Quadratic Bezier curve (in addition to the starting point, two more points are needed)
ctx.bezierCurveTo(x1, y1, x2, y2, x3, y3); // cubic Bezier curve (in addition to the starting point, three points are required)

// Set the style
ctx.fillStyle = 'red' // set the fill color
ctx.strokeStyle = 'blue' // set the fill color
ctx.lineWidth = 3 // set the line width
ctx.font = '24px blackbody'

ctx.fillText('entity text', text display x, text display y); // set text
ctx.strokeText('Hollow text', text display x, text display y); // set text

// coordinate translation && rotation && zoom
ctx.translate(100, 100) // Modify the coordinate origin (coordinate translation)
ctx.rotate(Math.PI) // Rotate (the unit is radians and is rotated according to the origin of the coordinates)
ctx.scale (x multiple, y multiple) // Zoom

// Save and use the previous coordinate system
ctx.save() // Save the previous coordinate system (you can save the translation data of the coordinate system, scale the data, rotate the data)
ctx.restore() // restore the previous coordinate system

// clear the canvas
ctx.clearRect(x, y, width, height)

// Reopen a path
ctx.beginPath()

ctx.closePath() // Close the path to close for one path
Ctx.stroke() // build path
Ctx.fill() // build fill path
```
---

###  Other operations

```js
// Fill the image (the fill of the texture is filled with the origin of the coordinate system)
let img = new Image()
img.src = 'https://google.com/img/bus.png'
img.onload = function () {
    ctx.translate(100, 100)
    ctx.fillStyle = ctx.createPattern(img, 'no-repeat')
    ctx.fillRect(0, 0, 100, 100)
}

// linear gradient fill
let bg = ctx.createLinearGradient(100, 100, 200, 200);
bg.addColorStop(0, 'white'); // gradient starting point
bg.addColorStop(1, 'black'); // The end of the gradient (of course, the value of multiple stages can also be written in the middle)
ctx.fillStyle = bg
ctx.fillRect(100, 100, 100, 100)

// Radiation gradient
let bg = ctx.createRadialGradient(150, 150, 0, 180, 180, 180)
bg.addColorStop(0, 'white'); // gradient starting point
bg.addColorStop(1, 'black'); // The end of the gradient (of course, the value of multiple stages can also be written in the middle)
ctx.fillStyle = bg
ctx.fillRect(100, 100, 100, 100)

// shadow
ctx.shadowColor = 'red'
ctx.shadowBlur = 10;
ctx.fillRect(100, 100, 100, 100)

// Rounded Rectangle
ctx.moveTo(100, 110) // The y-axis is 10 more, which is a trick
ctx.arcTo(100, 200, 200, 200, 10)
ctx.arcTo(200, 200, 200, 100, 10)
ctx.arcTo(200, 100, 100, 100, 10)
ctx.arcTo(100, 100, 100, 200, 10)
Ctx.stroke()
```
---

##  websocket

**Basic use**

```js

let socket = new WebSocket('http://...') // is using the http protocol

// This handler is called when the socket is fully open and ready to communicate.
Socket.onpen = function () {

}

// socket receives server message
Socket.onmessage = function (e) {

}

// send a message to the web service using postMessage()
socket.postMessage('Hello Server')

```

---


##   Local Storage

**localStorage: Each browser provides 5MB~10MB of space for local storage. It will not disappear unless it is deleted actively.**

```js

// to save
localStorage.setItem('key', 'value')

// to get
localStorage.getItem('key')

// attributes
localStorage.length // tell us how many data items localStorage has
localStorage.key(i) // Incoming index, you can get the data of the object (can be cycled together with length)

// method
localStorage.removeItem(key) // Clear the corresponding data item according to the key value
localStorage.clear() // will delete all data items associated with the current page
```

**sessionStorage: The supported APIs are exactly the same as above. The difference is that the locally stored data items will be deleted after the browser is closed.**

---

##  Geolocation

```js

// navigator.geolocation.getCurrentPosition (successful callback, failure callback, configuration parameters)

navigator.geolocation.getCurrentPosition( res => {
    console.log('successary callback: ', res)
    // res.coords.latitude latitude
    // res.coords.longitude longitude
}, err => {
    console.log('Failed callback: ', err)
})

```

---

##  Video 

```html
<!--
    The controls browser provides controls that allow the user to control the playback of video and audio.
    Autoplay autoplay
    Poster="Poster picture displayed when the video is not playing"
    Whether loop loops
    Preload finer grained control how to load video
    ...
-->
<video src="playback address" controls autoplay poster="poster image displayed when the video is not playing"></video>
```

```js

// Callback triggered by video loading completion
let video = document.getElementById('video')
video.addEventListener('ended', () => {
    // callback trigger
})

// ...
```

##  Additional content

### 1.Modernizer.js (Detecting browser support for an API | HTML5/CSS3 detection library)

[Modernizer official website] (https://modernizr.com/)
[Modernizer official documentation] (https://modernizr.com/docs)

```js
// example
if (Modernizr.webgl){
    Console.log('browser support webgl')
} else {
    Console.log ('Browser does not support webgl')
}
```

### 2. Offline web application

**Create a cache manifest file (cache, manifest, file)**

```html
<!-- Add the file name of the cache manifest file to the HTML tag -->
<html manifest="main.manifest">
```

**CACHE MANIFEST must start with this | CACHE indicates the file to be cached**

```js
CACHE MANIFEST
CACHE:
Main.html
Main.css
Main.js
```

**Note: If you are on the server, you also need to set the AddType text/cache-manifest .manifest line to provide the correct MIME type**

---