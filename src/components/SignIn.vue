<template>
  <div class='container'>
    <h1>Welcome</h1>
    <input type='email' placeholder='Email...' v-model='email'/>
    <input type='password' placeholder='Password...' v-model='password' id='password'/>
    <i id='toggler' @click.prevent='togglePassView' class="fas fa-eye"></i>
    <main-btn @click.prevent='signin' textContent='SIGN IN'/>
    <notification v-if='msg' :msg='msg'/>
  </div>
</template>

<script>
import { ref } from 'vue';
import MainBtn from './MainBtn.vue';
import Notification from './Notification.vue';

export default {
  name: 'SignIn',
  components: { MainBtn, Notification },
  setup() {
    const email = ref('');
    const password = ref('');
    const msg = ref('');
    /* eslint-disable */
    const togglePassView = () => {
      const input = document.querySelector('#password');
      const icon = document.querySelector('#toggler');
      if (input.getAttribute('type') === 'password') {
        input.setAttribute('type', 'text');
        icon.classList.add('fa-eye-slash');
      } else {
        input.setAttribute('type', 'password');
        icon.classList.remove('fa-eye-slash');
      };
    };
    const signin = async () => {
      try {
        const data = await fetch('http://localhost:3001/signin', {
          method: 'post',
          headers: { 'content-type': 'application/json' },
          body: JSON.stringify({ email: email.value, password: password.value }),
        })
        const formatData = await data.json();
        msg.value = formatData;
        formatData.ok && localStorage.setItem('user', email.value);
      } catch (error) {
        console.log(error);
      };
    };
    return { email, password, msg, togglePassView, signin };
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
    padding-bottom: 10px;
    font-weight: 100;
  }
  input {
    margin: 5px 0;
    outline: none;
    border: none;
    padding: 10px;
    border-radius: 3px;
  }
}
</style>
