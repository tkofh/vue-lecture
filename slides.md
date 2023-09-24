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

Tim Morris - UConn CSE 2xxx - 9/19/23

---

# Agenda

- speedy intro to web dev
  - html
  - css
  - javascript
- installation
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

# language: **h**yper**t**ext **m**arkup **l**anguage

- v old
- markup language: tags & attributes
- "structure & content" of a webpage

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
url: https://stackblitz.com/edit/js-yigmp7?embed=1&file=index.html
---

---

# language: **c**ascading **s**tyle **s**heets

- also v old
- selectors & rules
- "style" of a webpage
- not liked

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
url: https://stackblitz.com/edit/js-jezfw7?embed=1&file=style.css
---

---

# technology: web browser

- large
- main (only?) portal to "the web"
- built on a "browser engine"
- features such as
  - bookmark management
  - ad tracking interference

---
layout: full-image
image: safari-chrome.png
---

---

# technology: browser engine

---
layout: section
---

# intro to vue

---
layout: big-points
---

- templates & single-file components
- reactivity
- forms
- data fetching

---

# templates

```vue {all|1-3|5-7|9-13} {lines:true}
<template>
  <h1>Hello World!</h1>
</template>

<script setup lang="ts">
console.log("hi");
</script>

<style scoped>
h1 {
  color: rebeccapurple;
}
</style>
```

---

layout: iframe
url: https://stackblitz.com/edit/vitejs-vite-mscofq?embed=1&file=src%2FApp.vue&hideExplorer=1&hideNavigation=1

---
