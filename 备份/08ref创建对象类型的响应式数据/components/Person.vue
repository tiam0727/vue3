<template>
  <div class="person">
    <h2>一辆{{ car.brand }}车，价值{{ car.price }}万 </h2>
    <button @click="changePrice">修改汽车价格</button>
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
import {ref} from 'vue'

let car = ref({brand: '奔驰', price: 100})

//游戏列表
let games = ref([
  {id: 'aaa01', name: '王者'},
  {id: 'aaa02', name: '原神'},
  {id: 'aaa03', name: 'lol'},
  {id: 'aaa04', name: 'ra3'},
])

//方法
function changePrice() {
  car.value.price += 1
}

function changeFirstGame() {
  games.value[0].name = '永劫无间'
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