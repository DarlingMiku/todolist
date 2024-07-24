<template>
    <form @submit.prevent="addTodo">
      <input
        type="text"
        :value="modelValue"
        @input="UpdatedInput"
        placeholder="Добавьте новое дело"
        class="maininput__newtodo"
      />
      <button type="submit" class="mainAdd">Добавить</button>
    </form>
  </template>
  
  <script>
  export default {
    props: {
      modelValue: {
        type: String,
        required: true
      }
    },
    methods: {
      UpdatedInput(event) {
        this.$emit('update:modelValue', event.target.value);
      },
      addTodo() {
        this.$emit('addTodo');
      }
    },
    emits: ['update:modelValue', 'addTodo']
  };
  </script>
  
  <style scoped>
  .maininput__newtodo {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border: 2px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    transition: 0.4s;
  }

  .maininput__newtodo:focus{
    border: 2px solid green;
    outline: none;    
  }

  .mainAdd {
    padding: 10px 20px;
    border: none;
    background-color: #28a745;
    color: white;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .mainAdd:hover {
    background-color: #218838;
  }

  form {
  border-bottom: 2px solid #46464682;
  padding-bottom: 10px;
}
  </style>