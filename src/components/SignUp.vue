<template>
  <div class='container'>
    <input type='email' placeholder='Email...' v-model='email'/>
    <input type='password' placeholder='Password...' v-model='password'/>
    <input type='password' placeholder='Repeat password...' v-model='repeatPassword'/>
    <button @click.prevent='signup'>Sign Up</button>
    <p>{{ msg.msg }}</p>
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
.container {
  display: flex;
  flex-direction: column;
}
</style>
