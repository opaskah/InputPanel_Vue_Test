<template>
    <div>
      <div v-for="(item, index) in items" :key="index" class="row">
        <!-- Use the Dropdown component -->
        <Dropdown v-model="item.criteria" :options="criteriaOptions" />
  
        <!-- TextInput component -->
        <TextInput v-model="item.input" />
  
        <!-- Delete button -->
        <DeleteButton @delete="removeField(index)" />
      </div>
      <button @click="addField" class="add-btn">+ Add Item</button>
    </div>
</template>
  
<script>
  import { ref, computed } from "vue";
  import Dropdown from "./Dropdown.vue";
  import TextInput from "./TextInput.vue";
  import DeleteButton from "./DeleteButton.vue";
  
  export default {
    props: {
      modelValue: {
        type: Array,
        default: [],
      },
    },
    components: {
      Dropdown,
      TextInput,
      DeleteButton,
    },
    setup(props, { emit }) {
      const criteriaOptions = ref([
        "Age",
        "Education",
        "Interest",
        "Language",
        "Marital Status",
        "Skill",
      ]);
  
      const items = computed({
        get: () => props.modelValue,
        set: (newValue) => emit("update:modelValue", newValue),
      });
  
      const addField = () => {
        items.value.push({ criteria: "", input: "" });
      };
  
      const removeField = (index) => {
        items.value.splice(index, 1);
      };
  
      return {
        criteriaOptions,
        items,
        addField,
        removeField,
      };
    },
  };
  </script>
  
  