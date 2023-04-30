<script >
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
  <BarChart />

  <RouterView />
</template>

<style>
html,
body,
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 62.5%;
  color: #000;
}
:root {
  /*Colors*/
  --light-blue: #3f51b5;
  --dark-blue: #303f9f;
  --purple: #7c4dff;
  --light-amber: #ffc107;
  --dark-amber: #ffa000;
  --orange: #ff5722;
  --gray: #252c30;
  --black: #000;

  /*Typography*/
  --h1: 7.594rem;
  --h2: 5.063rem;
  --h3: 3.375rem;
  --h4: 2.25rem;
  --h5: 1.5rem;

  /*Intentions*/
}
nav{
  font-size: var(--h2);
  text-align: center;
}
</style>
