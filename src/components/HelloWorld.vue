<script setup lang="ts">
import { computed, onMounted, reactive, toRefs, ref, watch } from "vue";

interface Props {
  name: string;
  age?: number;
}

const props = defineProps<Props>();

const { name, age } = toRefs(props);

interface Emits {
  (e: "onEmit", id: number): void;
  (e: "otherEmit", payload: string): void;
}

// interface Emits {
//   onEmit: [id: number];
//   otherEmit: [payload: string];
// }

const emit = defineEmits<Emits>();
const defaults = [
  { name: "kivanc", age: 13 },
  { name: "Samet", age: 32 },
];
const other = { name: "tuce", age: 24 };

const a = ref(structuredClone(defaults));
const b = reactive(structuredClone(defaults));

const addToRef = () => {
  a.value.push(structuredClone(other));
};

const addToReactive = () => {
  b.push(structuredClone(other));
};

const c = computed(() => {
  return b.map((item) => item.name);
});

watch(name, (newVal, oldVal) => {
  console.log(newVal, oldVal);
});

onMounted(() => {
  console.log(props);
  console.log(name.value);
  console.log(age);
});
</script>

<template>
  <h1>{{ name }}</h1>
  <h2>{{ age }}</h2>

  <div class="card">
    <button type="button" @click="addToRef">Ref</button>
    <button type="button" @click="addToReactive">REACt</button>
    <div>
      {{ a }}
    </div>
    <div>
      {{ b }}
    </div>
    <div>{{ c }}</div>
  </div>
  <button @click="emit('onEmit', 1)">Emit 1</button>
  <button @click="emit('otherEmit', 'test')">Emit 2</button>
</template>
