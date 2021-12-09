<template>
  <div class='container'>
    <h1>Welcome</h1>
    <input type='email' placeholder='Email...' v-model='email'/>
    <input type='password' placeholder='Password...' v-model='password'/>
    <button @click.prevent='signin'>Sign In</button>
    <notification v-if='msg' :msg='msg'/>
  </div>
</template>

<script>
import { ref } from 'vue';
import Notification from './Notification.vue';

export default {
  name: 'SignIn',
  components: { Notification },
  setup() {
    const email = ref('');
    const password = ref('');
    const msg = ref('');
    /* eslint-disable */
    const signin = async () => {
      await fetch('http://localhost:3001/signin', {
        method: 'post',
        headers: { 'content-type': 'application/json' },
        body: JSON.stringify({ email: email.value, password: password.value }),
      })
      .then(async (data) => msg.value = await data.json())
      .catch((error) => console.log(error));
    };
    return { email, password, msg, signin };
    /* eslint-enable */
  },
};
</script>

<style scoped lang='scss'>
@import '../assets/variables';

.container {
  display: flex;
  flex-direction: column;
  background-color: $BlueColor;
  box-shadow: -2px 2px 10px $BlackDarkColor;
  padding: 20px;
  width: 300px;
  text-align: center;
  border-radius: 3px;
  color: $Gray200Color;
  h1 {
    padding: 10px 0;
    font-weight: 100;
  }
  input {
    margin: 5px 0;
    outline: none;
    border: none;
    padding: 10px;
    border-radius: 3px;
  }
  button {
    margin: 10px 0;
    outline: none;
    border: none;
    padding: 10px;
    border-radius: 3px;
    font-weight: 700;
    transition:  .2s;
    background-color: $Gray200Color;
    color: $BlackDarkColor;
  }
  button:hover {
    cursor: pointer;
    background-color: $BlackDarkColor;
    color: $Gray200Color;
  }
}
</style>
