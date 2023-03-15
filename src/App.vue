<script >
  import Calculator from './components/Calculator.vue'

  export default{
    name: `App`,
    components:{
      Calculator,
    }
  }
</script>

<template>
  <Calculator />
</template>

<style >
  body{
    background-color: gray;
    margin-top: 250px;
  }
</style>
