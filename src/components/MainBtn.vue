<template>
  <button>{{ textContent }}</button>
</template>

<script>
export default {
  name: 'MainBtn',
  props: ['textContent'],
};
</script>

<style scoped lang='scss'>
@import '../assets/variables';

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
</style>
