<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import { ref } from "vue";
const name = ref("kivanc");
const handleEmit = (id: number) => {
  console.log(id);
};

const handleEmit2 = (payload: string) => {
  console.log(payload);
};
</script>

<template>
  <HelloWorld @on-emit="handleEmit" @other-emit="handleEmit2" :name="name" />
  <button @click="name = 'tuce'">PRESSSSSSS</button>
</template>
