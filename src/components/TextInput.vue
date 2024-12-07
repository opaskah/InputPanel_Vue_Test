<template>
    <input
      :value="modelValue" 
      @input="updateValue($event.target.value)" 
      type="text"
      placeholder="Enter value"
      class="text-input"
    />
  </template>
  
  <script>
  export default {
    props: {
      modelValue: {
        type: String, // The input value passed as a prop
        default: "",
      },
    },
    emits: ["update:modelValue"], // Emit this event when the value changes
    methods: {
      updateValue(newValue) {
        // Emit the updated value to the parent
        this.$emit("update:modelValue", newValue);
      },
    },
  };
  </script>
  
  <style scoped>
  .text-input {
    padding: 5px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  </style>
  