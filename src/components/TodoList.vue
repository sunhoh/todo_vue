<template>
  <div>
    <transition-group name="list" tag="ul">
      <li 
        v-for="(list, index) in todoList" 
        :key="index" 
        :class="{done: list.status === 'done'}"
      >
        <!-- //완료 -->
          <i 
          v-if="list.status === 'created'"
          class="fas fa-check checkBtn" 
          @click="$emit('statusControl', index, 'done')" />
          
        <!-- //부활 -->
          <i
          v-else
          class="fas fa-redo-alt checkBtn" 
          @click="$emit('statusControl', index, 'created')"/>
  
        <!-- 리스트 -->
        <span>{{list.todo}}</span>

        <!-- //수정 || 삭제 -->
        <span class='editOrremoveBtn'>
          <!-- //수정 -->
          <i 
            v-if="list.status ==='created'"
            class="fas fa-edit" 
          />
          <!-- //삭제 -->
          <i 
            class="fas fa-trash-alt "
            @click="$emit('listDelete', index)" />
        </span>        
      </li>
    </transition-group>
  </div>
</template>

<script>
// import { eventBus } from '../main'

export default {
    props:['todoList'],
    // methods: {
    //   //state함수
    //   listEdit(memo, index){
    //     //부모에서 가져온 함수
    //     eventBus.listEdit(memo, index)
    //   }
    // }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  justify-content: space-between;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}

.checkBtn {
  padding:5px;
  line-height: 40px;
  color: #62acde;
  margin-right: 5px;
  cursor: pointer;
}

.editOrremoveBtn {
  padding:0 5px 0 5px;
}
.editOrremoveBtn i:nth-child(1) {
  color: #35495e;
  cursor: pointer;
}
.editOrremoveBtn i:nth-child(2) {
  margin-left: 10px;
  color: #de4343;
  cursor: pointer;
}

.done {
  background: rgba(0, 0, 0, 0.1);
}
.done span{
  text-decoration: line-through;
  color: rgba(0, 0, 0, 0.5);
}

/* 리스트 아이템 트렌지션 효과 */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from, .list-leave-to  {
  opacity: 0;
  transform: translateY(30px);
}
</style>
