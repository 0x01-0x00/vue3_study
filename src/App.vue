<template>
  <hr/>
  <h1 class="rootClass">根组件</h1>
  <h3>ref()->reactive():{{ refObj }}</h3>
  <button @click="changeRefObj">点击整体赋值</button>
  <h3>reactive()无法整体赋值:{{ reactiveObj }}</h3>
  <button @click="changeReactiveObj">点击整体赋值失效</button>
  <button @click="changeReactiveValue">点击只能修改属性值</button>
  <hr/>
  <h3>toRef():{{ toRefObj }}</h3>
  <button @click="changeToRefValue">点击</button>

  <hr/>
  <MyChild fatherData="父数据">
    <template v-slot:childSlot1>
      <div>子组件插槽</div>
    </template>
  </MyChild>
  <hr/>
</template>

<script>
  import MyChild from "./pages/MyChild.vue";
  import {reactive, ref, toRef} from "vue";

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
        alert("丢失响应式！！！")
        console.log(reactiveObj)
      }
      function changeReactiveValue() {
        if (reactiveObj.name === "响应式数据reactiveObj") {
          reactiveObj.name = "响应式数据reactiveObj->change"
        } else {
          reactiveObj.name = "响应式数据reactiveObj"
        }
        console.log(reactiveObj)
      }


      let toRefObj = reactive({name: "响应式数据toRefObj", array: [1, 2, 3]})
      let toRefObj_name = toRef(toRefObj, "name")

      function changeToRefValue() {
        console.log(toRefObj_name)
        if (toRefObj.name === "响应式数据toRefObj") {
          toRefObj_name.value = "响应式数据toRefObj->Change"
        } else {
          toRefObj_name.value = "响应式数据toRefObj"
        }
        console.log(toRefObj_name)
      }

      return {
        refObj,
        reactiveObj,
        toRefObj,
        changeRefObj,
        changeReactiveObj,
        changeReactiveValue,
        changeToRefValue
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
