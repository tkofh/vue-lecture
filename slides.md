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

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/HTML)

```html {all|1|9|2-8|5}
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
layout: iframe
url: https://stackblitz.com/edit/web-platform-q8zphy?embed=1&file=index.html
---

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

# resource: images

```html
<img src="/example.png" alt="example alt text" />
```

- `src` is the path to the image
- `alt` is the text describing the picture to visually impaired

<div class="h-8"></div>

```html
<picture>
  <source srcset="/example-portrait.jpg" media="(orientation: portrait)" />
  <img src="/example-landscape.jpg" alt="" />
</picture>
```

- browser only requests one image, based on environmental conditions

links:
- [mdn docs for `img`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)
- [mdn docs for `picture`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture)

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

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/CSS)

```css {all|1|2|7|12}
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
layout: iframe
url: https://stackblitz.com/edit/web-platform-q8cluc?embed=1&file=index.html
---

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

- implements ecmascript standard
- implements tc39 specification
- famously created in 17 days (and it shows! jk)
- no relation to java

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

```js
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
layout: iframe
url: https://stackblitz.com/edit/js-hssz58?embed=1&file=index.js
---

---

# technology: dom

- document object model
- enables js modification of the html on screen

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

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
layout: iframe
url: https://stackblitz.com/edit/web-platform-m1cjh1?embed=1&file=script.js
---

---

# web api: fetch

- js api for making http requests
- can interpret json, binary data, anything the browser can interpret

[mdn docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

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
layout: iframe
url: https://stackblitz.com/edit/web-platform-vd4cir?embed=1&file=script.js
---

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

---
layout: iframe
url: https://stackblitz.com/edit/vitejs-vite-zafbgh?embed=1&file=counter.js
---

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
layout: iframe
url: https://stackblitz.com/edit/vitejs-vite-y4rosg?embed=1&file=src%2Fcomponents%2FAppHeader.vue
---
