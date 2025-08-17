<template>
  <h1 class="rootClass">根组件</h1>
  <h2>ref()->reactive():{{ refObj }}</h2>
  <button @click="changeRefObj">点击整体赋值</button>
  <h2>reactive()无法整体赋值:{{ reactiveObj }}</h2>
  <button @click="changeReactiveObj">点击整体赋值失效</button>
  <button @click="changeReactiveValue">点击只能修改属性值</button>

  <MyChild fatherData="父数据">
    <template v-slot:childSlot1>
      <div>子组件插槽</div>
    </template>
  </MyChild>
</template>

<script>
  import MyChild from "./pages/MyChild.vue";
  import {reactive, ref} from "vue";

  export default {
    setup() {
      let refObj = ref({name: "响应式数据refObj", array: [1, 2, 3]})
      let reactiveObj = reactive({name: "响应式数据reactiveObj", array: [1, 2, 3]})

      function changeRefObj() {
        if (refObj.value.name === "响应式数据refObj") {
          refObj.value = {name: "响应式数据refObj->Change", array: [4, 5, 6]}
        } else {
          refObj.value = {name: "响应式数据refObj", array: [1, 2, 3]}
        }
        console.log(refObj)
      }
      function changeReactiveObj() {
        if (reactiveObj.name === "响应式数据reactiveObj") {
          reactiveObj = {name: "响应式数据reactiveObj->Change", array: [4, 5, 6]}
        } else {
          reactiveObj = {name: "响应式数据reactiveObj", array: [1, 2, 3]}
        }
        console.log(refObj)
      }
      function changeReactiveValue() {
        if (reactiveObj.name === "响应式数据reactiveObj") {
          reactiveObj.name = "响应式数据reactiveObj->change"
        } else {
          reactiveObj.name = "响应式数据reactiveObj"
        }
        console.log(reactiveObj)
      }

      return {
        refObj,
        reactiveObj,
        changeRefObj,
        changeReactiveObj,
        changeReactiveValue
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
