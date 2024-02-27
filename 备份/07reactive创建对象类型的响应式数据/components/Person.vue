<template>
  <div class="person">
    <h2>一辆{{car.brand}}车，价值{{car.price}}万 </h2>
    <button @click="changePrice">修改汽车价格</button>
    <br>
    <h2>游戏列表：</h2>
    <ul>
      <li v-for="g in games" :key="g.id">{{g.name}} </li>
    </ul>
    <button @click="changeFirstGame">修改第一个游戏</button>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Person',
  // data() {
  //   return {
  //     name: '张三',
  //     age: 18,
  //     tel: '15888888888'
  //   }
  // },
  // methods: {
  //   showTel() {
  //     alert(this.tel)
  //   },
  //   changeName() {
  //     this.name = "zhang-san"
  //   },
  //   changeAge() {
  //     this.age += 1
  //   }
  // }
  // setup() {
  //   //数据，原先是写在data当中的
  //   //注意此时的name，age，tel不是响应式的
  //   let name = '张三'
  //   let age = 18
  //   let tel = '15888888888'
  //
  //   //方法
  //   function changeName() {
  //     name = 'zhang-san'//注意这样修改了name，但是页面没有改变
  //   }
  //
  //   function changeAge() {
  //     age += 1
  //   }
  //
  //   function showTel() {
  //     alert(tel)
  //   }
  //   //模板需要使用的数据或方法需要交出去
  //   return {name, age ,changeName,changeAge,showTel}
  //
  // }
}
</script>

<script lang="ts" setup>
import {reactive} from 'vue'
let car=reactive({brand:'奔驰',price:100})

//游戏列表
let games=reactive([
  {id:'aaa01',name:'王者'},
  {id:'aaa02',name:'原神'},
  {id:'aaa03',name:'lol'},
  {id:'aaa04',name:'ra3'},
])
//方法
function changePrice() {
   car.price+=1
}

function changeFirstGame(){
  games[0].name='永劫无间'
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