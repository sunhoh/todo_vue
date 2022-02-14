<template>
    <div class="inputBox">
      <!-- // 인풋 -->
      <input 
        type="text" 
        v-model="todo" 
        @keyup.enter="addTodo"
      />
      <!-- //추가버튼 -->
      <span class="addContainer" @click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
    </div>
</template>

<script>

export default {
  props: {
    header: String,
    body: String,
  },

  data() {
      return {
        todo: '',
      }
  },
  methods: {
      addTodo() {
      this.todo !== ''  
      && this.$emit('addTodo', this.todo)
         this.todo =''
      },
  },
}
</script>

<style scoped>
input:focus {
 outline: none;   
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  width: 50%;
  padding: 10px;
  border-style: none;
  font-size: 0.9rem;
  
}

.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
}

.addBtn {
  color: white;
  vertical-align: middle;
}

.closeModalBtn {
  color: #42b983;
}
</style>