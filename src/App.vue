<template>
  <div>
    <div class='page-group'>
      <div class='page page-current' id='main'>
        <Header></Header>
        <div class='content'>
          <div class='content-block'>
            <div v-for='(item,index) in list' :key="index">
              <Item :items="list" :item="item" :index="index"></Item>
            </div>
          </div>
        </div>
      </div>

      <div class='page' id='edit'>
        <Edit :items="list"></Edit>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import Item from './components/item'
import Edit from './components/edit'

export default {
  name: 'app',
  data(){
    return{
      list:[
        {
          "title": "TODOList",
          "content": "吃饭",
          "date": "2018年1月7日 20:38"
        },
        {
          "title": "uyuyu",
          "content": "睡觉",
          "date": "2018年1月8日 22:48"
        }
      ]
    }
  },
  components: {
    Header,
    Item,
    Edit
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
