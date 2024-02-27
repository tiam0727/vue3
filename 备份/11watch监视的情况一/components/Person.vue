<template>
  <div class="person">
    <h2>
      当前求和为:{{ sum }}
    </h2>
    <button @click="changeSum">点我修改sum值</button>
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
let sum: any = ref(0)

function changeSum() {
  sum.value += 10

}

//监视
//情况一：监视【ref】定义的【基本类型数据】
const stopWatch = watch(sum, (newValue, oldValue) => {
  console.log("sum变化了 ", newValue, oldValue)

  //停止监视的条件
  if (newValue >= 100) {
    stopWatch();
  }
})
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