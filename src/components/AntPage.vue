<template>
  <el-container>
    <el-header class="header">Header</el-header>
    <el-container>
      <el-aside class="aside" width="200px">Aside</el-aside>
      <el-main class="main">Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  name: "AntPage",
  data() {
  },
  computed: {},
  props: {},
  methods: {},
  mounted() {
  }
}
</script>

<style scoped>
.header{
  background: #aaaaaa;
}
.aside{
  background: #42b983;
}
.main{
  background: pink;
}
</style>