<template>
  <div class="container">
    <img alt="Vue logo" src="./assets/logo.png">  
    <TodoHeader />
    <TodoInput 
      @addTodo='addTodo' 
      :todoList='todoList'
    /> 
    <TodoList 
      :todoList='todoList'
      @statusControl='statusControl'
      @listDelete='listDelete' />
    <TodoFooter 
      @clearAll='clearAll' />
  </div>
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
      this.todoList.push({todo: todo, status: 'created', seleted: false})
       },

    statusControl(index, status){ this.todoList[index].status = status },

    listDelete(index){ this.todoList.splice(index, 1) },

    clearAll(){ this.todoList = [] }
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
  background-color: #f6f6f6;
}
.container {
  margin: 0 auto;
  max-width: 50rem;
  text-align: center;
}
input {
  border-style: groove;
  border:1px solid black;
}
button { border-style: groove; }

.shadow { box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03); }
</style>


