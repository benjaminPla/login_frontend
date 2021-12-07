<template>
  <div class='container'>
    <input type='email' placeholder='Email...' v-model='email'/>
    <input type='password' placeholder='Password...' v-model='password'/>
    <button @click.prevent='signin'>Sign In</button>
    <p>{{ msg.msg }}</p>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'SignIn',
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
.container {
  display: flex;
  flex-direction: column;
}
</style>
