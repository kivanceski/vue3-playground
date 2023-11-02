<template>
  <div class="example-component">
    <!-- Your template goes here -->
    <h1>{{ message }}</h1>
  </div>
</template>

<script lang="ts">
export default {
  name: "ExampleComponent",
  data() {
    return {
      // Your component's data
      message: "Hello, Vue 3!",
    };
  },
};
</script>
