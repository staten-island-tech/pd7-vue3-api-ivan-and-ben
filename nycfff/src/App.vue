<script >
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <div class="wrapper">
      <h1>NYC Funny Fun Facts</h1>
      <p id="description">Welcome to New York City Funny Fun Facts! Click on the bar below to switch datasets. </p>
      <nav>       
          <div id="router"><RouterLink to="/">Air Quality</RouterLink></div>
          <div id="router"><RouterLink to="/about">Baby Names</RouterLink></div>
      </nav>
    </div>
  </header>

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
h1{
  font-size: var(--h1);
  text-align: center;
}
#description{
  font-size: var(--h4);
  text-align: center;
}
nav{
  font-size: var(--h2);
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
}
#router{
  margin: 1rem;
}
.chart{
  width: 75%;
  margin: auto;
}
</style>
