<template>
  <h1>根组件</h1>
  <MyChild fatherData="父数据"/>
</template>

<script>
  import MyChild from "./pages/MyChild.vue";

  export default {
    setup() {
      return {
      }
    },
    components: {
      MyChild
    }
  }
</script>

<style scoped>
</style>
