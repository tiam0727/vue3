<template>
  <div class="person">
    <h2>一辆{{ brand }}车，价值{{ price }}万 </h2>
    <button @click="changePrice">修改汽车价格</button>
    <button @click="changeName">修改汽车品牌</button>
    <button @click="changeCar">修改汽车</button>
    <br>
    <h2>游戏列表：</h2>
    <ul>
      <li v-for="g in games" :key="g.id">{{ g.name }}</li>
    </ul>
    <button @click="changeFirstGame">修改第一个游戏</button>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Person',

}
</script>

<script lang="ts" setup>
import {reactive, toRef, toRefs} from 'vue'

let car = reactive({brand: '奔驰', price: 100})

//游戏列表
let games = reactive([
  {id: 'aaa01', name: '王者'},
  {id: 'aaa02', name: '原神'},
  {id: 'aaa03', name: 'lol'},
  {id: 'aaa04', name: 'ra3'},
])

// let brand: any =toRef(car,"brand")
// let price: any =toRef(car,"price")
let {brand,price}:any = toRefs(car)
//方法
function changePrice() {
  price.value += 1
}
function changeName() {
  brand.value = '宝马'
}
function changeCar() {

  //car={brand: '奥托',price: 10}//这么写页面不更新
  //car=reactive({brand: '奥托',price: 10})//这么写页面不更新

  //下面这种写法页面可以更新
  Object.assign(car,{brand: '奥托',price: 10})
}

function changeFirstGame() {
  games[0].name = '永劫无间'
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