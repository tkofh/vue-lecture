---
theme: vuetiful
highlighter: shiki
lineNumbers: false
transition: fade
title: Intro to Vue.JS
mdc: true
---

# Front End Web Dev With Vue.js

Tim Morris - UConn CSE 2xxx - 9/19/23

---

# Agenda

- speedy intro to web dev
- quick history of vue.js
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
console.log('hi');
</script>

<style scoped>
h1 {
  color: rebeccapurple;
}
</style>
```

---
layout: iframe

# the web page source
url: https://stackblitz.com/edit/vitejs-vite-mscofq?file=src%2FApp.vue
---
