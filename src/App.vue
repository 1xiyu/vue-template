<template>
  <div id="app">
    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew" name="">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
import Store from './store'
console.log(Store)
// vue的一些参数和属性
export default {
 /* components: {
    Hello
  }*/
  data:function(){
    return {
      title:'this is a todo list',
      items:Store.fetch(),
      newItem:''
    }
  },
  methods:{
    toggleFinish:function(item){
      item.isFinished = !item.isFinished;
    },
    addNew:function(){
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
      this.newItem = '';
    }
  },
  watch:{
    items:{
      handler:function(items){
        Store.save(items)
      },
      deep:true
    }
  }
}
</script>

<style>
.finished{
  text-decoration: underline;
}
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
