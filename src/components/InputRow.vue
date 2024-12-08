<template>
    <div class="input-row">
      <!-- Dropdown for selecting criteria -->
      <select v-model="localCriteria" class="dropdown">
        <option disabled value="">Select</option>
        <option v-for="option in criteriaOptions" :key="option" :value="option">
          {{ option }}
        </option>
      </select>
  
      <!-- Input field -->
      <input v-model="localInput" placeholder="Free text" class="input-field"/>
  
      <!-- Delete button -->
      <button @click="removeRow" class="delete-btn">X</button>
    </div>
  </template>
  
<script>
  export default {
    props: {
      criteria: {
        type: String,
        default: "",
      },
      input: {
        type: String,
        default: "",
      },
    },
    data() {
      return {
        // Local data to for the criteria and input
        localCriteria: this.criteria,
        localInput: this.input,
        // Dropdown options
        criteriaOptions: ["Age", "Education", "Interest", "Language", "Marital Status", "Skill"],
      };
    },
    watch: {
      // Emit changes back to the parent when local data changes
      localCriteria(newVal) {
        this.$emit("update:criteria", newVal);
      },
      localInput(newVal) {
        this.$emit("update:input", newVal);
      },
    },
    methods: {
      // Notify parent to delete this row
      removeRow() {
        this.$emit("remove");
      },
    },
  };
</script>


<style scoped>

/* Style for the row */
.input-row {
  padding: 10px;
  font-family: monospace;
  background-color: rgb(255, 255, 255);
  border: 2px dashed #cccccc;
  display: flex;
  align-items: center;
  margin-bottom: 0;
}

/* Style for the input dropdown */
.dropdown {
  flex: 1;
  padding: 8px;
  margin-right: 5px;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: rgb(255, 255, 255);
  color: #000000;
  font-size: 14px;
}

/* Style for the input field */
.input-field {
  flex: 2;
  padding: 8px;
  margin-right: 5px;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: rgb(255, 255, 255);
  color: #777777;
  font-size: 14px;
}

/* Style for the delete button */
.delete-btn {
  background-color: rgb(215, 0, 0);
  font-family: monospace;
  color: white;
  border: none;
  padding: 7px 14px;
  cursor: pointer;
  border-radius: 4px;
  font-size: 20px;
}

.delete-btn:hover {
  background-color: darkred;
}

</style>
  