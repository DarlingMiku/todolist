<template>
  <li>
    <input
      type="checkbox"
      v-model ="this.isChecked.checked"
      @change="updateCheckbox"
      class="checkbox-box"
    />
    <p :class="this.isChecked">{{ todo.value }}</p>
    <button @click="removeTodo(todo.index)" class="mainbutton__delete">Удалить</button>
  </li>
</template>

<script>
export default {

  data(){
  return{ 
    isChecked: {
          checked:false
        },
  }
},

  name: "ThePoint",
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    updateCheckbox(event) {
      this.$emit('update:isChecked', { index: this.todo.index, isChecked: event.target.checked });
    },
    removeTodo(index) {
      this.$emit('remove', index);
    },
    checkedThrough(){
      
    },
  },
  emits: ["remove", "update:isChecked"]
};
</script>

<style scoped>
.mainbutton__delete {
  padding: 5px 10px 5px 10px;
  border: none;
  background-color: #28a745;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  height: 35px;
  margin-left: 10px;
}

.mainbutton__delete:hover {
  box-shadow: 0px -6px 0 #1eae01 inset;
}

li {
  list-style-type: none;
  display: flex;
  align-items: center;
}

.maininput__checkbox {
  margin-right: 10px;

}

.checked{
  transition: 0.2ms;
  text-decoration: line-through;
}

.checkbox-input {
    display: none;
}

.checkbox-box {
    width: 20px;
    height: 20px;
    border: 2px solid green;
    border-radius: 4px;
    margin-right: 8px;
    position: relative;
}

.checkbox-input:checked + .checkbox-box {
    background-color: green;
}

.checkbox-input:checked + .checkbox-box::after {
    content: '';
    display: block;
    width: 6px;
    height: 10px;
    border: solid white;
    border-width: 0 2px 2px 0;
    transform: rotate(45deg);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) rotate(45deg);
}

</style>