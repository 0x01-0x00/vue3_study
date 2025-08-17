<template>
  <div>
    <h1>子组件{{fatherData}}</h1>
    <button @click="getFatherData">点击获取父组件数据</button>
  </div>
</template>

<script>
  export default {
    // 父组件给子组件传递数据
    props: ["fatherData"],
    setup(props, context) {
      // 获取父组件数据
      function getFatherData() {
        console.log("子组件获取父组件数据")
        console.log("props: ", props)
        console.log("context: ", context)
      }
      return {
        getFatherData
      }
    },
  }
</script>

<style>

</style>
