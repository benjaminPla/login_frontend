<template>
  <nav-bar />
  <router-view/>
  <footer-bar />
</template>

<script>
import NavBar from './components/NavBar.vue';
import FooterBar from './components/FooterBar.vue';

export default {
  name: 'App',
  components: { NavBar, FooterBar },
};
</script>

<style lang='scss'>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>
