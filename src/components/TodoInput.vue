<template>
    <div class="inputBox">
      <input type="text"  v-on:keyup.enter="addTodo">
      <span class="addContainer" v-on:click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
      <Modal v-if="showModal" @close="showModal = false">
          <h3 v-bind="header">
              경고 
              <i class="fas fa-times closeModalBtn" @click="showModal=false"></i>
          </h3>
            <div :v-bind="body">무언가를 입력하세요</div>
      </Modal>
    </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
  props: {
	header: String,
    body: String,
	// default: 'props를 안내려줘도 이 값이 뜸'
  },

  data() {
      return {
        newTodoItem:'',
        showModal: false
      }
  },
  methods: {
      addTodo() {
        if(this.newTodoItem !== ''){
            this.$emit('addTodoItem', this.newTodoItem)
            this.clearInput();
        } else {
           this.showModal = !this.showModal; 
        }  
      },
      clearInput() {
          this.newTodoItem = '';
      }
  },
  components:{ Modal }  
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