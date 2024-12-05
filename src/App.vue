<template>
  <div id="app">
    <!-- Title for the page "InputPanel Component"-->
    <h1 class="title">InputPanel Component</h1>

    <!-- InputPanel Component -->
    <div class="center-container">
      <input-panel v-model="items" />
    </div>

    <!-- Display the generated data/items (sama seperti yang di soal testnya)-->
    <h3 class="title2">&lt;input-panel v-model="items"/&gt;</h3>
    <pre class="generated-data">
      [
      {{ items.map(item => JSON.stringify(item)).join(",\n  ") }}
      ]
    </pre>
  </div>
</template>

<script>
// Importing ref
import { ref } from "vue";
import InputPanel from './components/InputPanel.vue';

// The default export is the Vue component definition for the App component, with the component being InputPanel
export default {
  name: 'App',
  components: {
    InputPanel,
  },
  setup() {
    // Reactive array to store the generated items
    const items = ref([]);

    // Return reactive data to be used in the template
    return {
      items,
    };
  },
};
</script>

<style>
/* White colour background for the page */
:root {
  background-color: #ffffff;
}

/* Style for the Container for InputPanel Component */
.center-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Style for the generated data/items display */
.generated-data {
  color: black;
  font-family: monospace;
  font-size: 16px;
}

/* Style for the title "InputPanel Component" */
.title {
  text-align: center;
  margin-top: 20px;
  font-size: 24px;
  font-family: Arial, sans-serif;
  color: black;
}

/* Style for the title "InputPanel Component" */
.title2 {
  color: black;
}

</style>