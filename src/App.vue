<template>
  <h1 class="title">我是根组件</h1>
  <button @click="fn">点击</button>
  <MyChild/>
</template>

<script>
  import MyChild from './pages/MyChild.vue'
  export default {
    data() {
      return {
        msg: 'app'
      }
    },
    methods: {
      fn() {
        alert('点击了')
      }
    },
    components: {
      MyChild
    }
  }
</script>

<style scoped>
  .title {
    color: red;
  }
</style>
