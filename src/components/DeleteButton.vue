<template>
    <button @click="onDelete" class="delete-btn">X</button>
  </template>
  
  <script>
  export default {
    emits: ["delete"], // Emits a 'delete' event when clicked
    methods: {
      onDelete() {
        this.$emit("delete");
      },
    },
  };
  </script>
  
  <style scoped>
  .delete-btn {
    background-color: red;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 5px 10px;
    cursor: pointer;
  }
  </style>
  