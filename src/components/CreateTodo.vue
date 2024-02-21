<script setup>
const props = defineProps({
  items: [],
});

console.log(props.items);
</script>

<template>
  <div class="mb-2">
    <input
      type="text"
      placeholder="todo"
      class="border-solid border-2 border-slate-500"
    />
    <button class="px-4 border-solid border-2 border-slate-500">Submit</button>
  </div>
</template>
