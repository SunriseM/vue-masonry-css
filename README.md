A new masonry component powered by CSS to be fast loading and free of jQuery or other dependacies. Build specifically for Vue projects.

[todo image]

### 😎 Why?

Existing solutions like Vue wrapped DeSandro Masonry, while great had downfalls in our Vue app. It required rendering the DOM on load and on during resize before determining the layout which lead to a slow, laggy experiance that would occasionally break the layout completely during resize. It also had dependancies on jQuery and while being feature packed it showed in the large file size.

To combat this, we looked into the latest techniques using just CSS, including flexbox & grid which fell short for anything other than basic images. CSS columns came the closest though the ordering reflow (orders down each column before reflowing to the next) visually broke when working with large different sized  elements.

Plain ol, div columns to the rescue!

*`vue-masonry-css`* Is a Vue Component with a simple interface to order items into the desired columns at specified breakpoints. With minimal CSS this leads to a quick, reliable solution that also has great browser support along with rendering performance.

#### 🏳️ What doesn't this do

* Animate when sorting (..we're keeping it simple here)
* Work with elements of different widths
* Box algorithm (not really needed if your elements have the same width)
* Break when resizing (at least, thats the goal)
* Load and render the DOM before sorting out the layout <= actually thats the plus!

#### 😄 What does this do
* Responsive! ..always
* IE 9+ CSS Support
* Depedancy & jQuery free
* CSS powered (Fast loading & Performant)
* Gutters


### 😲 Simple Usage

Add `vue-masonry-css` to your project:

By script..

```HTML
<script src="https://unpkg.com/vue"></script>
<script src="https://unpkg.com/vue-masonry-css"></script>
```

Or as a module... `npm install vue-masonry-css --save-dev`

```JS
import Vue from 'vue'
import VueMasonry from 'vue-masonry-css'

Vue.use(VueMasonry);
```

In your HTML template...
```HTML
<masonry
  :cols="3"
  :gutter="'30px'"
  >
  <div v-for="(item, index) in items" :key="index">Item: {{index + 1}}</div>
</masonry>
```

### Notes

- At the moment, only works with `v-for="..` child elements with `:key="`
- Does not work with `<transition-group />`

Both of these drawbacks are due to how Vue renders child elements and the ideal masonry layout technique we're aiming to use. _(I'm looking for workarounds with any help from the community!)_

### Resposive Breakpoints

Different columns and gutter sizes can be specified by passing an object containing key's of the window widths and their values representing the number of columns or gutter size. To have a fallback value, use the `default` key.

_note:_ The `cols=` attribute needs to use Vues bind method to evaluate objects. Instead of `cols=""` use either `v-bind:cols="{ 700: 3 }"` or the shorthand `:cols="{ 700: 3 }"`

```HTML
<masonry
  :cols="{default: 4, 1000: 3, 700: 2, 400: 1}"
  :gutter="{default: '30px', 7000: '20px'}"
  >
  <div v-for="(item, index) in items" :key="index">Item: {{index + 1}}</div>
</masonry>
```

### Suggestions & Issues
https://github.com/paulcollett/vue-masonry-css

**Contact me direct:**
* https://github.com/paulcollett
* http://paulcollett.com
