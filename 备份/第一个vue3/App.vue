<script  lang="ts">
import Person from './components/Person.vue'
export default {
  name: 'App',//组件名
  components: {Person}//注册组件
}
</script>

<template>
  <div class="app">
    <h1>你好啊！</h1>
    <Person />
  </div>
<!--  <Person />-->
</template>

<style scoped>
.app {
  box-shadow: 0 0 10px;
  background: #dddddd;
  border-radius: 10px;
  padding: 100px;
}

</style>
