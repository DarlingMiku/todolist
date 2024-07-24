<template lang="">
  
     <ul>
      <TransitionGroup name="list" tag="ul">
        <ThePoint
        v-for="todo in todos"
        :todo="todo"
        :key="todo.index"
        @remove="remove"
        />
      </TransitionGroup>
      </ul>
    
</template>


<script>
import ThePoint from './ThePoint.vue';

export default {
    name:"ThePoints",
    props:{
      todos:{
        type:Array,
        required:true
      }
    },
    components:{
      ThePoint
    },
    emits:["remove"],

    methods:{
        remove(index) {
            this.$emit('remove', index);
        }
    }
} 
</script>

<style scoped>
    .list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>