<template>
  <nav>
    <img src='../assets/logo.png' alt='logo' />
    <div>
      <router-link class='route' to="/">Sign In</router-link>
      <router-link class='route' to="/signup">Sign Up</router-link>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
};
</script>

<style scoped lang='scss'>
@import '../assets/variables';

nav {
  width: 100vw;
  background: $BlueColor;
  position: fixed;
  top: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 20px;
  img {
    width: 40px;
  }
  .route {
    margin: 0 10px;
  }
}
</style>
