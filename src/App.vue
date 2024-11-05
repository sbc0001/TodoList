<template>
<div id="app">
  <TodoList/>
</div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList,
  }
}
</script>

<style>
html,body{
  background-color:rgba(154,190,200,0.7);
}
#app{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width:85%;
  min-height:150px;
  margin:0 auto;
  padding-bottom:10px;
}
</style>
