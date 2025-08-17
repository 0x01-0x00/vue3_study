<template>
  <h1 class="root">根组件</h1>
  <MyChild fatherData="父数据">
    <template v-slot:childSlot1>
      <div>子组件插槽</div>
    </template>
  </MyChild>
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
  .root {
    color: red;
  }
</style>
