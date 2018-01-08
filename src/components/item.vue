<template>
  <div class='card' v-bind:class="{done:isDone}">
      <div class='card-header'>
        <a href="#edit">
          <span class='card-title' @click='modifyItem(index)'>{{item.title}}</span>
        </a>
        <input name='check' type='checkbox' @click='isDone=!isDone'/>
      </div>
      <div class='card-content' v-show="item.content!=''">
        <div class='card-content-inner'>{{item.content}}</div>
      </div>
      <div class='card-footer'>
        <span class='data'>{{item.data}}</span>
        <a><span class='icon icon-remove' @click='delItem(index)'></span></a>
      </div>  
  </div>
</template>

<script>
import bus from "./../eventBus.js"
export default {
  props:["items","item","index"],
  data(){
    return{
      isDone:false,
      itemList:this.items
    }
  },
  watch:{
    items(val){
      this.itemList = val;
    },
    itemList(val){
      this.$emit("items-changed",val);
    }
  },
  method:{
    delItem:function(){
      $.confirm("delect?",()=>{
        this.itemList.splice(index,1);
      });     
    },
    modifyItem:function(){
        bus.$emit("modify-item",index);
      }
  }
}
</script>

<style>
.card-content-inner {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.card-title {
  color: #333;
  font-weight: bold;
}
.date {
  font-size: 0.5rem;
}
.done {
  color: #CCC;}

.card-title {
  color: #CCC;
  text-decoration: line-through;
  text-decoration-color: #999;
  -moz-text-decoration-color: #999;}
  

</style>
