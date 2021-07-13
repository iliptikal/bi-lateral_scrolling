<template>
  <div id="app">
    <Bumper />
    <HorizontalScrollSection>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
      <div class="element"></div>
    </HorizontalScrollSection>
    <Bumper />
  </div>
</template>

<script>
import Bumper from "./components/Bumper.vue";
import HorizontalScrollSection from './components/HorizontalScrollSection.vue';

export default {
  name: 'App',
  components: {
    Bumper,
    HorizontalScrollSection
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 1.6rem;
}
.element {
  background: linear-gradient( to bottom, #117634 40%, #042c02 95%);
  height: 40rem;
  width: 50rem;
  margin: 0 2rem 0 0;
}
</style>
