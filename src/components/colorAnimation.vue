<template>
  <div class="box">

  </div>
</template>

<script>
export default {
  name: "colorAnimation"
}
</script>

<style scoped>
  .box{
    width: 100px;
    height: 100px;
    background: black;
    animation: ani 1s infinite linear;
  }
  @keyframes ani {
    0%{transform: rotate(0deg) }
    /*12.5%{transform: rotate(90deg)}*/
    /*25%{transform: rotate(135deg)}*/
    100%{transform: rotate(360deg)}
    /*0%{transform: rotate(0deg)}*/
  }
</style>