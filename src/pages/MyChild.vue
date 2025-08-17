<template>
  <div class="childClass">
    <h1>子组件{{fatherData}}</h1>
    <slot name="childSlot1">子组件插槽数据</slot>
    <button @click="getFatherData">点击获取父组件数据</button>
  </div>
</template>

<script>
  export default {
    // 父组件给子组件传递数据
    // props是响应式对象，不建议解构
    // context是非响应式对象，可以安全解构
    props: ["fatherData"],
    setup(props, context) {
      // 获取父组件数据
      function getFatherData() {
        console.log("子组件获取父组件数据")
        console.log("props: ", props)
        console.log("context: ", context)
        console.log("childSlot1: ", context.slots.childSlot1)
      }
      return {
        getFatherData
      }
    },
  }
</script>

<style scoped>
  .childClass {
    color: green;
  }
</style>
