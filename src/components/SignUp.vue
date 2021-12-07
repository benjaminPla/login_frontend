<template>
  <div class='container'>
    <h1>Welcome</h1>
    <input type='email' placeholder='Email...' v-model='email'/>
    <input type='password' placeholder='Password...' v-model='password'/>
    <input type='password' placeholder='Repeat password...' v-model='repeatPassword'/>
    <button @click.prevent='signup'>Sign Up</button>
    <p v-if='msg'>{{ msg.msg }}</p>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'SignUp',
  setup() {
    const email = ref('');
    const password = ref('');
    const repeatPassword = ref('');
    const msg = ref('');
    /* eslint-disable */
    const signup = async () => {
      if (password.value === repeatPassword.value) {
        await fetch('http://localhost:3001/signup', {
          method: 'post',
          headers: { 'content-type': 'application/json' },
          body: JSON.stringify({ email: email.value, password: password.value }),
        })
        .then(async (data) => msg.value = await data.json())
        .catch((error) => console.log(error));
      };
    };
    return { email, password, repeatPassword, msg, signup };
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
    padding: 5px;
    border-radius: 3px;
    background-color: $LightBlueColor;
    color: $BlackDarkColor;
    font-weight: 700;
  }
}
</style>
