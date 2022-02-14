<template>
    <div class="inputBox">
      <!-- // 인풋 -->
      <input type="text" v-model="memo" />
      <!-- //추가버튼 -->
      <span class="addContainer" @click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
      
    </div>
</template>

<script>
// import Modal from './common/Modal.vue'

export default {
  props: {
	header: String,
    body: String,
	// default: 'props를 안내려줘도 이 값이 뜸'
  },

  data() {
      return {
        memo:null,

        newTodoItem:'',
        showModal: false
      }
  },
  methods: {
      addTodo() {
       console.log('리스트 추가')
       if(this.memo === ''){
        alert('할일 입력 바람')
       }else {
        this.$emit('addTodo', this.memo)
       }

      },
      
  },
  // components:{ Modal }  
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