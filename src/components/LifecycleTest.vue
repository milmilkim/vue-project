<script>
export default {
  mounted() {
    //마운트(렌더링)된 후 실행될 코드

    // const $span = document.createElement('span');
    // $span.textContent = "비밀이야";

    this.$refs.star.textContent = 'Bye World!!!';
  },
  data() {
    return {
      text: 'text',
    };
  },
};
</script>

<template>
  <p ref="star">heum</p>
</template>
