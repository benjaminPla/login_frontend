<template>
  <nav>
    <router-link to="/">Sign In</router-link> |
    <router-link to="/signup">Sign Up</router-link>
  </nav>
  <router-view/>
</template>

<style lang='scss'>
@import './assets/variables';

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  // background-color: $CyanColor;
}
</style>
