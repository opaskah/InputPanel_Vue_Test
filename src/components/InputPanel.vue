<template>
  <div class="input-panel">
    <!-- Add Item Button -->
    <button @click="addField" class="add-item">+ Add Item</button>

    <!-- Inputs -->
    <div v-for="(item, index) in items" :key="index" class="input-group">
      <!-- Input dropdown for criteria, e.g. "Age", "Education", etc -->
      <select v-model="item.criteria" class="dropdown">
        <option disabled value="" class="select">Select</option>
        <option v-for="option in criteriaOptions" :key="option" :value="option">
          {{ option }}
        </option>
      </select>

      <!-- Input for value, free text -->
      <input
        v-model="item.input"
        placeholder="Enter value (Free text)"
        class="input-field"
      />
      <!-- Remove button/"X" button -->
      <button @click="removeField(index)" class="remove-button">X</button>
    </div>
  </div>
</template>

<script>
export default {
  // `props` is used to define the properties passed into this component from a parent component
  props: {
    modelValue: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    // Two-way binding for v-model
    items: {
      get() {
        return this.modelValue;
      },
      set(newValue) {
        this.$emit("update:modelValue", newValue);
      },
    },
  },
  data() {
    return {
      // Options for the criteria dropdown
      criteriaOptions: ["Age", "Education", "Interest", "Language", "Marital Status", "Skill"],
    };
  },
  methods: {
    addField() {
      // Add a new field with empty values
      this.items.push({ criteria: "", input: "" });
    },
    removeField(index) {
      // Remove the field at the given index
      this.items.splice(index, 1);
    },
  },
};
</script>

<style scoped>
/* Style for the InputPanel */
.input-panel {
  padding: 20px;
  max-width: 600px;
  margin: auto;
  font-family: Arial, sans-serif;
  background-color: rgb(255, 255, 255);
  border: 2px dashed #ccc;
  border-radius: 8px;
}

/* Style for the Add Item button */
.add-item {
  display: block;
  margin-left: 200px;
  margin-bottom: 20px;
  background-color: blue;
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 4px;
}

/* Add hover effect for the Add Item button */
.add-item:hover {
  background-color: darkblue;
}

/* Style for the input */
.input-group {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

/* Style for the input dropdown */
.dropdown {
  flex: 1;
  padding: 8px;
  margin-right: 5px;
  border: 1px solid #ccc;
  background-color: rgb(255, 255, 255);
  color: black;
}

/* Style for the input field */
.input-field {
  flex: 2;
  padding: 8px;
  margin-right: 5px;
  border: 1px solid #ccc;
  background-color: rgb(255, 255, 255);
  color: black;
}

/* Style for the remove button, the "X" button */
.remove-button {
  background-color: red;
  color: white;
  border: none;
  padding: 8px;
  cursor: pointer;
  border-radius: 4px;
  font-size: 16px; /* Larger "X" */
}
</style>
