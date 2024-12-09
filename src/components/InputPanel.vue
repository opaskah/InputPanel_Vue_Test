<template>
  <div class="input-panel">
    <!-- Add Item button -->
    <button @click="addItem" class="add-item">+ Add Item</button>
    <div v-for="(item, index) in items" :key="item.id">
      <InputRow
        v-model:criteria="item.criteria"
        v-model:input="item.input"
        @remove="removeItem(item.id)"
      />
    </div>
  </div>
</template>

<script>
import InputRow from "./InputRow.vue";

export default {
  // Registers the InputRow as a child of InputPanel
  components: {
    InputRow,
  },
  
  props: {
    modelValue: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    items: {
      get() {
        return this.modelValue;
      },
      set(newValue) {
        this.$emit("update:modelValue", newValue);
      },
    },
  },
  methods: {
    addItem() {
      // Add a new row with an id
      this.items.push({ id: Date.now(), criteria: "", input: "" });
    },
    removeItem(id) {
      // Remove the row by id
      this.items = this.items.filter(item => item.id !== id);
    },
  }
};
</script>


<style scoped>
/* Style for the InputPanel */
.input-panel {
  padding: 20px;
  max-width: 600px;
  margin: auto;
  font-family: Arial, Helvetica, sans-serif;
  background-color: white;
  border: 2px dashed #ccc;
}

/* Style for the Add Item button */
.add-item {
  font-family: Arial, Helvetica, sans-serif;
  display: block;
  margin-left: 240px;
  margin-bottom: 20px;
  background-color: rgb(59, 129, 214);
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 14px;
  cursor: pointer;
  border-radius: 4px;
}

.add-item:hover {
  background-color: darkblue;
}

</style>
