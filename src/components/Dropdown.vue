<template>
    <select
      :value="modelValue"
      @change="updateValue($event.target.value)"
      class="dropdown"
    >
      <option disabled value="">Select</option>
      <option v-for="option in options" :key="option" :value="option">
        {{ option }}
      </option>
    </select>
  </template>
  
  <script>
  export default {
    props: {
      modelValue: {
        type: String, // The currently selected value
        default: "",
      },
      options: {
        type: Array, // The list of dropdown options
        required: true,
      },
    },
    emits: ["update:modelValue"], // Emit this event for two-way binding
    methods: {
      updateValue(newValue) {
        this.$emit("update:modelValue", newValue); // Notify the parent of the new value
      },
    },
  };
  </script>
  
  <style scoped>
  .dropdown {
    padding: 5px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  </style>
  