<template>
  <div id="app">
    <h1>{{msg}}</h1>
    <ol class="olStyle">
      <li v-for="(item,index) in items" :class="{'IsFinash': item.isFanished}">
        <input type="checkbox" v-model="item.isFanished"/>
        {{item.label}}
        <button @click="delItem(index)">Del</button>
      </li>
    </ol>
    <input v-model="newItem"/>
    <button @click="addNewItem">Add</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      msg: 'Todo List',
      items: [],
      newItem: [],
    }
  },
  methods:{
    addNewItem: function () {
      this.items.push({label: this.newItem, isFanished: false});
      this.newItem = [];
    },
    delItem:function (index) {
      this.items.splice(index, 1)
      console.log('del')
    }
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
  .olStyle{
    list-style-type: none;
  }
  .IsFinash{
    text-decoration: line-through;
  }
</style>
