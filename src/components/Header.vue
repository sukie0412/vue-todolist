<template>
  <header>
    <h1 class='title'>tooooo</h1>
    <a class='icon icon-edit pull-right' href='#edit' @click='addItem'></a>
  </header>
</template>

<script>
import bus from './../eventBus.js'

export default{
  methods:{
    addItem:function(){
      bus.$emit("add-item")
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
