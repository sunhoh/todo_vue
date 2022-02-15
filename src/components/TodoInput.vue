<template>
    <div class="inputBox">
      <!-- // 인풋 -->
      <input 
        type="text" 
        v-model="value" 
        @keyup.enter="addTodo"
      />
      <!-- //추가버튼 -->
      <span class="addContainer" @click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
      <Modal v-if="showModal" >
        <template v-slot:header> 
          <h3>경고 
            <i class="fas fa-times closeModalBtn" @click="showModal=false"/>
          </h3>
        </template>
        <template v-slot:body>
          <div>무언가를 입력하세요!</div>
        </template>
      </Modal>
    </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
  data() {
      return {
        value: '',
        showModal:false,
      }
  },
  methods: {
      addTodo() {
      if(this.value !== ''  ){
        this.$emit('addTodo', this.value)
        this.value =''
      } else {
        this.showModal = !this.showModal;
      }
    },
  },
  components: { Modal }
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
  cursor: pointer;
}
</style>