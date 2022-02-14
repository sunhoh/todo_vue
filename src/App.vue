<template>
  <img alt="Vue logo" src="./assets/logo.png">  
  <TodoHeader></TodoHeader>
  <TodoInput @addTodo='addTodo' /> 
  <TodoList 
  :todoList='todoList'
  @statusControl='statusControl'
  @listDelete='listDelete' />
  <TodoFooter></TodoFooter>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data() {
    return {
      todoList: [],
    }
  },
  methods:{
    addTodo(todo) {
      this.todoList.push({todo: todo, status: 'created'})
    },
    statusControl(index, status){
      this.todoList[index].status = status
    },
    listDelete(index){
      this.todoList.splice(index, 1)
    }
    
  },
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  }
}
</script>




<style>
body {
  text-align: center;
  background-color: #f6f6f6;
}
input {
  border-style: groove;
  width: 200px;
}
button { border-style: groove; }

.shadow { box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03); }
</style>
