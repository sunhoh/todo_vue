<template>
  <img alt="Vue logo" src="./assets/logo.png">  
  <TodoHeader></TodoHeader>
  <TodoInput @addTodo='addTodo'></TodoInput>
  <TodoList 
  :todoList='todoList'
  @statusControl='statusControl'></TodoList>
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
    addTodo(memo) {
      console.log('받았어')
      this.todoList.push({memo: memo, status: 'created'})
    },
    statusControl(index, status){
      this.todoList[index].status = status
    },
    
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
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
