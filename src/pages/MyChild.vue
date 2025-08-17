<template>
  <div>
    <h1>子组件{{fatherData}}</h1>
    <button @click="getFatherData">点击获取父组件数据</button>
  </div>
</template>

<script>
  export default {
    props: ["fatherData"],
    setup(props) {
      function getFatherData() {
        console.log(props)
        console.log(props.fatherData)
      }
      return {
        getFatherData
      }
    },
  }
</script>

<style>

</style>
