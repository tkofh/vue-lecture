---
theme: vuetiful
highlighter: shiki
lineNumbers: false
transition: fade
title: Intro to Vue.JS
mdc: true
---

<!-- markdownlint-disable-file -->

# Front End Web Dev With Vue.js

Tim Morris - UConn CSE 2xxx - 9/26/23

---

# Agenda

- speedy intro to web dev
  - browsers
  - http
  - html
  - css
  - javascript
- tools & local setup

---

# Agenda

- vue basics
  - component syntax
  - reactivity
  - building forms
  - fetching data
- routing
- deploying

---
layout: section
---

# speedy intro to (front end) web dev

---

# technology: web browser

- large app
- main portal to "the web"
- built on a "browser engine"
- features such as
  - bookmark management
  - ad tracking interference

---
layout: full-image
image: safari-chrome.png
---

---
layout: full-image
image: firefox-edge.png
---

---
layout: full-image
image: brave-arc.png
---


---

# technology: browser engine

- program that "implements the web"
  - fetching resources
  - parsing & resources
  - implements platform apis
  - renders pages
  - leverage engine to execute javascript
- implementation governed by the w3c

---
layout: full-image
image: engines-timeline.png
---

---
layout: full-image
image: browsers-and-engines.png
---

---

# organization: w3c

- world wide web consortium
- publishes open standards
- organized into "working groups"

---

# trivia: w3c v "the vendors"

- w3c publishes standards, but vendors implement them
- no obligation to implement standards
  - pressure comes from competition
- sus behavior
  - apple implements features useful to apple
  - google barely needs to compete

---

# protocol: http

- hypertext transfer protocol
- (generally) built upon tcp/ip: transmission control protocol/internet protocol
  - also tls: transport layer security
- enables transfer of documents from servers to clients

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/HTTP)

---

# language: **h**yper**t**ext **m**arkup **l**anguage

- "structure & content" of a webpage
- markup language: tags & attributes
- tags can provide functionality or semantic meaning

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/HTML)<br>
[playground](https://stackblitz.com/edit/web-platform-q8zphy?file=index.html)

```html {all|1|9|2-8|5} {maxHeight:'14rem'}
<header>
  <h1>My Site</h1>
  <nav>
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/about">About</a></li>
    </ul>
  </nav>
</header>
<main>
  <h2>Home Page</h2>
  <section>
    <p>Hello audience!</p>
  </section>
</main>
```

---

# sub-resources

- html document might reference other assets ("files")
- browser engine manages http requests for these assets
- depending on the way it is requested, engine does different things
- examples
  - images
  - videos / audio files
  - fonts
  - 3d models
  - stylesheets
  - scripts

---

# resource: stylesheet

- css document that influences how the webpage is rendered
- can also add animation, create 3d layouts, etc
- referenced via a `<link />` tag or declared inline via `<style>` tags in the `<head>` element:

```html
<html>
  <head>
    <link type="text/css" rel="stylesheet" href="/my-stylesheet.css" />

    <style type="text/css">
      /* ... */
    </style>
  </head>
</html>
```

---

# language: **c**ascading **s**tyle **s**heets

- selectors & rules
- "style" of a webpage
- not well liked (i like it tho)

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/CSS)<br>
[playground](https://stackblitz.com/edit/web-platform-q8cluc?file=index.html)

```css {all|1|2|7|12} {maxHeight: '14rem'}
header {
  background: blue;
  color: white;
  padding: 1rem;
}

header a {
  color: lime;
  font-weight: bold;
}

header a:hover {
  color: red;
}
```

---

# resource: script

- javascript file (or module)
- adds functionality to a webpage
- used to be optional, now required
- included via a `<script>` tag

```html
<html>
  <body>
    <script defer src="/my-script.js"></script>
    <script>
      // ...
    </script>
  </body>
</html>
```

---

# language: javascript

- implements ecmascript standard & tc39 specification
- famously created in 17 days (and it shows! jk)
- no relation to java

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)<br>
[mdn language overview](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_overview)<br>
[playground](https://stackblitz.com/edit/web-platform-djkwwe?file=index.html)

```js {maxHeight: '14rem'}
let angle = 0;

const pi = 3.1415926535;

function rotate(amount) {
  angle = (angle + amount) % (pi * 2);
  if (angle < 0) {
    angle += pi * 2;
  }
}

rotate(pi * 0.5);
```

---

# technology: dom

- document object model
- enables js modification of the html on screen

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)<br>
[playground](https://stackblitz.com/edit/web-platform-m1cjh1?file=script.js)

```js
window.addEventListener('click', () => {
  const messageElement = document.createElement('p');

  messageElement.appendChild(
    document.createTextNode('Hello World ' + Math.random())
  );

  document.body.appendChild(messageElement);
});
```

---

# web api: fetch

- js api for making http requests
- can interpret json, binary data, anything the browser can interpret

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)<br>
[playground](https://stackblitz.com/edit/web-platform-vd4cir?file=script.js)

```js
fetch('https://api.quotable.io/random')
  .then((res) => res.json())
  .then((data) => {
    console.log(data);

    const quoteElement = document.createElement('p');
    quoteElement.appendChild(
      document.createTextNode(`"${data.content}" - ${data.author}`)
    );

    document.body.appendChild(quoteElement);
  });
```

---

# what if...

- navigations between pages send a full html document
  - browser fetches all resources
- what if we loaded one document, with js that fetched new _content_?

---
layout: section
---

# tools & local setup

---

# technology: devtools

<img src="/devtools.png" class="w-full h-[30rem] -mt-6 object-contain" />

---

# technology: node.js

- javascript runtime
- enables javascript web servers, native apps, etc
- enables local tooling

[homepage](https://nodejs.org/en)

---

# technology: vite

- local development server
- bundler
  - optimizes html, css, js etc to maximize loading performance
  - humans care about spaces & newlines, the browser does not
- compiler

[playground](https://stackblitz.com/edit/vitejs-vite-zafbgh?file=main.js)

---
layout: section
---

# intro to vuejs

---

# background

- separation of concerns: structure, style, behavior
- components: logical grouping of structure, style & behavior
- "single page applications"

---

# single file components

- `*.vue` files
- reusable & composable
- declare props & slots

[vue docs](https://vuejs.org/guide/introduction.html)<br>
[playground](https://stackblitz.com/edit/vitejs-vite-y4rosg?file=src%2Fcomponents%2FAppHeader.vue)

```vue
<template>
  <header>
    <h1>My Site</h1>
    <!-- ... -->
  </header>
</template>

<script setup>
console.log('hello from this component!');
</script>

<style>
header {
  background: blue;
  color: white;
  padding: 1rem;
}
</style>
```

---

# declarative programming

- define what the result should be based on inputs
  - do not define the steps to take

```vue
<template>
  <p>{{ message }}</p>
</template>

<script setup>
const message = 'Hello, world!'
</script>
```

---

# control flow

- `v-if` enables conditional rendering

```vue
<template>
  <p v-if="showFirstMessage">First Message</p>
  <p v-else>Second Message</p>
</template>

<script setup>
const showFirstMessage = Math.random() > 0.5
</script>
```

---

# lifecycle hooks

- component creation
- `onMounted()`
- `onBeforeUnmount()`

```vue
<script setup>
import { onMounted, onBeforeUnmount } from 'vue'

console.log('I run instantly')

onMounted(() => {
  console.log('I run as soon as this component has html')
})

onBeforeUnmount(() => {
  console.log('I run just before this component loses its html')
})
</script>
```

---

# data binding

- declarative syntax
- `{{ }}` for text
- `v-bind` or `:` for data

```vue
<template>
  <h1 :id="id">{{ heading }}</h1>
</template>

<script setup>
const heading = 'Hello UConn'

const id = heading.toLowerCase().split(' ').join('-') // -> 'hello-uconn'
</script>
```
---

# event handlers

- `v-on:` and `@` syntax
- captures dom events
  - can also capture component events

[playground](https://stackblitz.com/edit/vitejs-vite-5ikkvm?file=src%2FApp.vue)

```vue
<template>
  <button @click="onButtonClick">Click Me!</button>
</template>

<script setup>
const onButtonClick = (event) => {
  console.log('The button was clicked', event)
}
</script>
```

---

# js primitives

- strings, numbers, booleans are all "primitives"
- passed by value not reference
- js objects _are_ passed by reference
- in order to "reference" a primitive, wrap it in an object

```js
const two = 2;
const number = two;

const twoObj = { value: 2 };
const numberObj = twoObj;
```

---

# reactivity: ref

- `ref` is an object with a `value` property
- when its `value` changes, vue knows it may need to update some things

```vue
<template>
  <p>the count is {{ count }}</p>
</template>

<script setup>
import { ref } from 'vue';

const count = ref(0);

setTimeout(() => {
  count.value = count.value + 1;
}, 1000);
</script>
```

[playground](https://stackblitz.com/edit/vitejs-vite-5ikkvm?file=src%2FApp.vue)

---

# reactivity: reactive

- sibling api to `ref`, allows properties other than `value`

```js
import { reactive } from 'vue';

const state = reactive({
  firstName: 'tim',
  passion: 'graphic design',
});
```
<div class="h-4"></div>

- difficult to read
```js
state.firstName
```

---

# reactivity: computed

- pure function producing some state based on other reactive values
- cached, smart

```vue
<template>
  <p>{{ fullName }}</p>
</template>

<script setup>
import { ref, computed } from 'vue';

const firstName = ref('tim')
const lastName = ref('morris')

const fullName = computed(() => `${firstName.value} ${lastName.value}`)
</script>
```

---

# reactivity: watch

- event listener for data changes
- can run side effects
- control over timing

```js
import { ref, watch } from 'vue';

const count = ref(0);

watch(count, (current, previous) => {
  console.log(`the current count is: ${current} (was ${previous})`);
});

// some time later...
count.value = 5;
```

---

# putting it all together

- `ref`, `computed`, `watch`, event handlers, and data binding can be combined to create almost any behavior
- these + browser APIs power most applications

[playground](https://stackblitz.com/edit/vitejs-vite-sg1sjm?file=src%2FApp.vue)

---

# form data binding

- data down, events up
- `<input />` elements have a `value` attribute (data down)
- `<input />` elements have an `input` event (events up)

```vue
<template>
  <input :value="firstName" @input="event => firstName = event.target.value" />
</template>

<script setup>
import { ref } from 'vue';
const firstName = ref('');
</script>
```

---

# form data binding

- this is so common it gets its own shorthand: `v-model`

```vue
<template>
  <input v-model="firstName" />
</template>

<script setup>
import { ref } from 'vue';
const firstName = ref('');
</script>
```

[playground](https://stackblitz.com/edit/vitejs-vite-ukxcgm?file=src%2FApp.vue)

---

# favor platform apis

if the platform offers an api for something, do not implement it yourself

don't do this:
```vue
<template>
  <form>
    <label>First Name <input v-model="firstName" />
    <button type="button" @click="onFormSubmit">Submit</form>
  </form>
</template>
```

do this:
```vue
<template>
  <form @submit.prevent="onFormSubmit">
    <label>First Name <input v-model="firstName" />
    <button type="submit">Submit</form>
  </form>
</template>
```

---

# fetch + vue

[playground](https://stackblitz.com/edit/vitejs-vite-8ejmze?file=src%2FApp.vue)

```vue {all|4,18|11-16|2,9,12|13|3,9,14|all}
<template>
  <p v-if="isLoading">Loading...</p>
  <p v-else>{{ quote }}</p>
  <button @click="loadQuote">Load Quote</button>
</template>

<script setup>
const quote = ref(null)
const isLoading = computed(() => quote.value === null)

function loadQuote() {
  quote.value = null
  fetch('https://api.quotable.io/random').then((res) => res.json()).then((data) => {
    quote.value = data.content
  })
}

onMounted(() => loadQuote())
</script>
```

---
layout: section
---

# scaling up

---

# routing

- leverages browser's history api to control url bar
- allows us to conditionally render vue components based on route state

[playground](https://stackblitz.com/edit/vitejs-vite-uvnfvq?file=src%2Fmain.js)

---

# deploying

- `vite build`
- upload `dist` folder to hosting provider (s3)

---
layout: section
---

# thank you!
