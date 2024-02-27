<template>
  <div class="person">
    <h2>姓名：{{ name }} name</h2>
    <h2>年龄：{{ age }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="showTel">查看联系方式</button>

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
  setup() {
    //setup函数中的this是undefined，vue3中开始弱化this
    //数据，原先是写在data当中的
    //注意此时的name，age，tel不是响应式的
    let name = '张三'
    let age = 18
    let tel = '15888888888'

    //方法
    function changeName() {
      name = 'zhang-san'//注意这样修改了name，但是页面没有改变
    }

    function changeAge() {
      age += 1
    }

    function showTel() {
      alert(tel)
    }
    //模板需要使用的数据或方法需要交出去
    return {name, age ,changeName,changeAge,showTel}

    //setup 的返回值也可以是一个渲染函数
    //return（）=>'哈哈'
  }
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