<template>
 <div>
   <h1>App 根组件</h1>
   <hr />
   <!-- <todo-list :list='todoList'></todo-list> -->
   <list-view></list-view>
 </div>
</template>

<script>
// import TodoList from './components/todo-list/TodoList.vue'
import ListView from './components/todo-list/ListView.vue'

export default {
  
  name: 'MyApp',
  data() {
    return {
      // todoList:[
      //   {id:1, task:'今天是星期一', done:false},
      //   {id:2, task:'今天是星期二', done:false},
      //   {id:3, task:'今天是星期三', done:true}
      //   ]
    }
  },
  components: {
    ListView
  }
}
</script>

<style lang='less' scoped>

</style>
