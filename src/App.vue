<template>
  <h1 class="rootClass">根组件</h1>
  <h2>ref():{{ obj }}</h2>
  <button @click="changeRef">点击</button>

  <MyChild fatherData="父数据">
    <template v-slot:childSlot1>
      <div>子组件插槽</div>
    </template>
  </MyChild>
</template>

<script>
  import MyChild from "./pages/MyChild.vue";
  import {ref} from "vue";

  export default {
    setup() {
      let obj = ref({name: "响应式数据src", array: [1, 2, 3]})

      function changeRef() {
        if (obj.value.name === "响应式数据src") {
          obj.value = {name: "响应式数据change1", array: [4, 5, 6]}
        } else {
          obj.value = {name: "响应式数据src", array: [1, 2, 3]}
        }
        console.log(obj)
      }

      return {
        obj,
        changeRef
      }
    },
    components: {
      MyChild
    }
  }
</script>

<style scoped>
  .rootClass {
    color: red;
  }
</style>
