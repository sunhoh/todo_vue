<template>
  <div>
    <transition-group name="list" tag="ul">
      <li 
        v-for="(list, index) in todoList" 
        :key="index" 
        v-bind:class="{done: list.status === 'done'}"
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
  
        <!-- //리스트 -->
        <span>{{list.memo}}</span>
        
        <!-- //삭제 -->
        <span class="removeBtn">
          <i class="fas fa-trash-alt"></i>
        </span>
      </li>
    </transition-group>
  </div>
</template>

<script>
export default {
    props:['todoList','toggle'],
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

.done {
  background: rgba(0, 0, 0, 0.1);
}
.done span{
  text-decoration: line-through;
  color: rgba(0, 0, 0, 0.5);
}


.removeBtn {
  margin-left: auto;
  color: #de4343;
}

</style>
