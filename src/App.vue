<template>
  <div id="app">
    <div id="nav">
      <div class="row">
        <h2 class="navBarTitle" style="padding: 1rem;"><strong>Yellow Bucket</strong></h2>
        <div id="spacer2">
          <router-link to="/"><img class="navBarImages" src="../public/MediaIcon.png"></router-link>
          <router-link to="/about"><img class="navBarImages" src="../public/AboutIcon.png"></router-link>
          <router-link to="/customers"><img class="navBarImages" src="../public/CustomerIcon.png"></router-link>
        </div>
      </div>
    </div>
    <div id="greeting">
      <h5><strong></strong></h5>
    </div>
    <router-view/>
  </div>
</template>

<script>

</script>

<style lang="scss">
  /* Add Google Font */
  @import url('https://fonts.googleapis.com/css?family=Open+Sans:300,400,700');
  /* This is where we inport our custom CSS files */
  @import './assets/styles/custom.css';

  #app {
    font-family: 'Open Sans', Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    background-color: #e5e5e5;
    color: #2c3e50;
  }
  #nav {
    padding: 48px;
    a {
      font-weight: bold;
      font-size: medium;
      color: #233140;
      &.router-link-exact-active {
        color: #ffff99;
      }
    }
  }
</style>
