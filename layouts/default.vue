<template>
  <div class="site-layout">
    <Navigation />
    <nuxt />
  </div>
</template>

<script>
import Navigation from '~/components/Navigation.vue'

export default {
  components: {
    Navigation
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat:900,900i|VT323&display=swap');

html {
  font-family: 'VT323';
  background-color: #252525;
  color: white;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

a {
  color: white;
}

input {
  background-color: transparent;
  box-shadow: none;
  border: none;
  border-bottom: 1px solid #94BD3D;
  color: white;
}

.site-layout {
 display: grid;
 grid-template-columns: 200px auto;
 padding: 1rem;
}
</style>
