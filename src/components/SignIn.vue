<template>
  <input type='email' placeholder='Email...' v-model='email'/>
  <input type='password' placeholder='Password...' v-model='password'/>
  <button @click.prevent='signin'>Sign In</button>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'SignIn',
  setup() {
    const email = ref('');
    const password = ref('');
    /* eslint-disable */
    const signin = async () => {
      await fetch('http://localhost:3001/signin', {
        method: 'post',
        headers: { 'content-type': 'application/json' },
        body: JSON.stringify({ email: email.value }),
      })
      .then(async (data) => console.log(await data.json()))
      .catch((error) => console.log(error));
    };
    /* eslint-enable */
    return { email, password, signin };
  },
};
</script>
