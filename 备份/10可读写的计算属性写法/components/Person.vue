<template>
  <div class="person">
    姓：<input type="text" v-model="firstName"/>
    名：<input type="text" v-model="lastName"/><br>
    全名：<span>{{ fullName }}</span><br>
    全名：<span>{{ fullName }}</span><br>
    全名：<span>{{ fullName }}</span><br>
    全名：<span>{{ fullName }}</span><br>
    全名：<span>{{ fullName }}</span><br>
    全名：<span>{{ fullName }}</span><br>
    <button @click="changeFullName"> 修改名</button>
  </div>
</template>

<script lang="ts">
export default {
  name: "Person",
};
</script>

<script lang="ts" setup>
import {computed, ref} from 'vue'

let firstName = ref("zhang");
let lastName = ref("san");
//这么定义的fullName是一个计算属性，且是只读的

// let fullName = computed(() => {
//   console.log(1)
//   return (
//       firstName.value.slice(0, 1).toUpperCase() +
//       firstName.value.slice(1) +
//       lastName.value
//   )
// })
let fullName = computed({
  get() {
    console.log(1)
    return (
        firstName.value.slice(0, 1).toUpperCase() +
        firstName.value.slice(1) +
        lastName.value
    )
  }
  ,
  //修改后的值
  set(val) {
    console.log('set',val)
    let [fir,last]= val.split('-')
    firstName.value=fir;
    lastName.value=last
  }
})

function changeFullName() {
  fullName.value = 'li-si'
}
</script>
<style scoped>
.person {
  background: skyblue;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}

button {
  margin: 15px;
}
</style>