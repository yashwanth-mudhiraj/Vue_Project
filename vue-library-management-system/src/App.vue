<!-- <script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> -->

<template>
  <div id="app">
    <button @click="count++">Increment {{ count }}</button>
    <button @click="count--">Decrement {{ count }}</button><br>
    <p>Student Name : {{ student.name }}</p>
    <p>Student ID : {{ student.id }}</p>
    <p>count2: {{ count2 }}</p>
    <p>count2: {{ state.count2 }}</p>
  

  <div :class="{active: isActive.val}"><p>Binding HTML class to data property </p></div>
  <button @click="changeClass">Change class</button>
</div>
</template>

<script setup lang="ts">

import { createApp, reactive, ref } from "vue";     // createApp creates a new application instance

const count = ref(0);                               // used for simple primitive reactive values
const state = reactive({count2:0})                  // used for complex reactive objects with multiple nested properties

let {count2} = state                                // destructuring data
count2++;

const student = reactive({
  name: "yash",
  id: 34566
})

let isActive = reactive({val : true});

function changeClass(){                             // function to change a data property of a class
  isActive.val = isActive.val ? false : true;
}

const app = createApp({
  setup() {                                         // reactive data and functions are configured in setup()
    return {
      count: count.value,
      count2,
      state : state.count2,
      isActive,
      changeClass
    };
  },
});

app.mount("#app");                                  // application instance should be mounted to ID attribute of div
</script>


<style>
.active {
  color: red;
  background-color: bisque;
}
</style>
