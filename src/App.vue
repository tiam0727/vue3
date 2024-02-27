<script  lang="ts">
import Person from './components/Person.vue'
export default {
  name: 'App',//组件名
  components: {Person}//注册组件
}
</script>

<template>
<!--  vue3可以同时书写多个标签-->
  <Person />
</template>

<style scoped>


</style>
