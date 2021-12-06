<template>
  <p>{{ user.msg }}</p>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  name: 'Home',
  setup() {
    const user = ref(null);
    /* eslint-disable */
    onMounted(async () => {
      await fetch('http://localhost:3001/signin', {
        method: 'post',
        headers: { 'content-type': 'application/json' },
        body: JSON.stringify({ email: 'benjaminpla.dev@gmail.com' }),
      })
      .then(async (data) => user.value = await data.json())
      .catch((error) => console.log(error));
      });
    /* eslint-enable */
    return { user };
  },
};
</script>
