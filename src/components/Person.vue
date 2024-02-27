<template>
  <div class="person">
    <h1>情况三：监视【reactive】定义的【对象类型数据】</h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <h2>汽车：{{ person.car.c1 }},{{ person.car.c2 }}</h2>

    <button @click="changeName">点我修改name</button>
    <button @click="changeAge">点我修改age</button>
    <button @click="changeC1">点我修改第一辆车</button>
    <button @click="changeC2">点我修改第二辆车</button>
    <button @click="changeCar">点我修改车</button>
  </div>
</template>

<script lang="ts">
export default {
  name: "Person",
};
</script>
<script lang="ts" setup>
import {reactive, watch} from "vue";
//数据
let person = reactive({
  name: 'Zhangsan',
  age: 18,
  car: {
    c1: '宝马',
    c2: '奔驰'
  }
})

//方法
function changeName() {
  person.name += '~'
}

function changeAge() {
  person.age += 1
}

function changeC1() {
  person.car.c1 = '奥迪'
}

function changeC2() {
  person.car.c2 = '大众'
}


function changeCar() {
  // person = {name: '李四', age: 90}
  //如果是被reactive包裹的对象需要修改应采用如下方式，可以保留响应式的特点
  // Object.assign(person, {name: '李四', age: 50})
  person.car = {c1: '雅迪', c2: '爱玛'}
}

//监视,情况3：监视【reactive】定义的【对象类型】数据，监视对象内部属性的变化，默认自动开启
/**
 * watch 的第一个参数是：被监视的数据
 * watch 的第二个参数是：监视的回调
 * watch 的第三个参数是：配置对象（deep、immediate等等）
 */
// watch(person, (newValue, oldValue) => {
//   console.log("person改变了", newValue, oldValue)
// })
//监视,情况4：监视响应式对象(ref/reactive定义的数据)中的某个属性（且为基本类型）需要将其转换为一个getter函数，即转化为()=>需要修改的值,这样的形式
// watch(() => person.name, (newValue, oldValue) => {
//   console.log("person.name变化了", newValue, oldValue)
// })
// 监视,情况4监视响应式对象(ref/reactive定义的数据)中的某个属性（且为对象类型），可以直接编也可以写成函数，【建议写成函数】
watch(()=>person.car, (newValue, oldValue) => {
  console.log("person.car改变了", newValue, oldValue)
},{deep:true})
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