<template>
  <nav>
    <img src='../assets/logo.png' alt='logo' />
    <div>
      <router-link
        @click.prevent='signout'
        class='route'
        to="/"
        v-if='user'>
          Sign Out
        </router-link>
      <div v-else>
        <router-link class='route' to="/">Sign In</router-link>
        <router-link class='route' to="/signup">Sign Up</router-link>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  setup() {
    const user = localStorage.getItem('user');
    const signout = () => localStorage.setItem('user', '');
    return { user, signout };
  },
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
    font-weight: 700;
    color: $Gray200Color;
    transition: 0.2s;
  }
  .route:hover {
    color: $BlackDarkColor;
  }
}
</style>
