# 3. JavaScript
---
Loading images, the old fashioned way:

```js
const img = new Image();

img.onload = () => {
  // insertion, followed by the image decode
  document.body.appendChild(img);  
};

// triggers loading
img.src = 'image.jpg';
```
---
But&hellip;

<img src="images/image-decode.png" width="1200" height="394" style="width: 100%; height: auto; padding: 10px; background: #fff; border: 1px solid #000">
---
The new and shiny way of loading images:

```js
const img = new Image();

// triggers load
img.src = 'image.jpg';

// queues decode
img.decode().then(function() {
  // This is guaranteed to paint the image without flicker 
  document.body.appendChild(img);
});
```

<p class="fragment">Works in Chromium and Safari</p>
---
And you can also use <code>.decode()</code> to feature test!

```js
const image = new Image();

image.src = 'image.webp';

image
  .decode()
  .then(() => {
    console.info('Supports WebP');
  })
  .catch(() => {
    console.warn('No WebP support');
  });
```
