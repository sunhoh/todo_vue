<template>
  <transition name="modal">
    <div :class="{'modal-mask': closeSeleter === false}"
      @click="closeModal"
    >
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header"> default header </slot>
          </div>
          <div class="modal-body">
            <slot name="body"> default body </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      closeSeleter: false
    }
  },
  methods: {
   closeModal(){
      console.log(this.closeSeleter)
      this.closeSeleter = !this.closeSeleter
   } 
  }
}
</script>

<style>
.modal-mask {
  position: fixed;
  z-index: 1000;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.modal-container {
  width: 300px;
  margin: 0px auto;
  padding: 30px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header {
  color: #42b983;
}
.modal-body {
  margin: 20px 0;
}

/* -------transition------- */
/* //작동하지 않음 공부 필요....  */
/* enter-active, leave-active은 자동으로 fade in or out 해준거 같음*/
/* 그래서 fade in or out 할때 transition 넣어줌*/
.modal-enter-active, .modal-leave-active {
  transform: scale(1.1);
  transition: opacity .5s ease;
}
.modal-enter, .modal-leave-to {
  opacity: 0;
}
/* -------transition------- */

</style>

