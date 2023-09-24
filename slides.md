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
layout: full-image
image: firefox-edge.png
---

---
layout: full-image
image: brave-arc.png
---


---

# technology: browser engine
