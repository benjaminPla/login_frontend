<template>
  <span class='msg' :class='msg.ok ? "success" : "fail"'>{{ msg.msg }}</span>
</template>

<script>
export default {
  name: 'Notification',
  props: ['msg'],
};
</script>

<style scoped lang='scss'>
@import '../assets/variables';

.msg {
  padding: 10px;
  border-radius: 3px;
}
.success {
  background-color: $GreenColor;
}
.fail {
  background-color: $RedColor;
}
</style>
