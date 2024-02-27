<template>
  <div class="person">
    <h1>
      情况二：监视【ref】定义的【对象类型数据】
    </h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="changeName">点我修改name</button>
    <button @click="changeAge">点我修改age</button>
    <button @click="changePerson">点我修改人</button>
  </div>
</template>

<script lang="ts">
export default {
  name: "Person",
};
</script>
<script lang="ts" setup>
import {ref, watch} from "vue";
//数据
let person = ref({
  name: 'Zhangsan',
  age: 18
})

//方法
function changeName() {
  person.value.name += '~'
}

function changeAge() {
  person.value.age += 1
}

function changePerson() {
  person.value = {name: '李四', age: 90}
}

//监视,情况一：监视【ref】定义的【对象类型】数据，监视的是对象的地址值，若想监视对象内部属性的变化，需要手动开启
/**
 * watch 的第一个参数是：被监视的数据
 * watch 的第二个参数是：监视的回调
 * watch 的第三个参数是：配置对象（deep、immediate等等）
 */
watch(person,(newValue,oldValue)=>{
  console.log("person改变了",newValue,oldValue)
},{deep:true,immediate:true})

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