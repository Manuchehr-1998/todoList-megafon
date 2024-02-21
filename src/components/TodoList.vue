<script setup>
import CreateTodo from "./CreateTodo.vue";
import { ref } from "vue";

const items = ref([
  {
    id: 1,
    title: "Test Megafon todolist vue 3 Tailwind Css",
  },
  {
    id: 2,
    title: "Test Megafon todolist vue 3 Tailwind Css",
  },
  {
    id: 3,
    title: "Test Megafon todolist vue 3 Tailwind Css",
  },
]);
</script>

<template>
  <CreateTodo :items="items" />
  <div class="w-4/5 m-auto">
    <table className="w-[92%] m-auto">
      <thead className="border-solid border-2 border-slate-500 p-2">
        <tr className="border-solid border-2  border-slate-500 p-2   ">
          <th className="border-solid border-2 border-slate-500 p-2">№</th>
          <th className="border-solid border-2 border-slate-500 p-2">Title</th>
          <th className="p-2 grid col-span-2 justify-center">Actions</th>
        </tr>
      </thead>
      <tbody class="border-solid border-2 border-slate-500 p-2">
        <tr
          class="border-solid border-2 border-slate-500 p-2"
          v-for="item in items"
          :key="item.id"
        >
          <td class="border-solid border-2 border-slate-500 p-2">
            {{ item.id }}
          </td>
          <td class="border-solid border-2 border-slate-500 p-2">
            {{ item.title }}
          </td>
          <td class="border-solid border-2 border-slate-500 p-2">Del</td>
          <td class="border-solid border-2 border-slate-500 p-2">Edit</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
