<script setup>
import { ref } from "vue";

const items = ref([]);
const newTodoTitle = ref("");
const editItemId = ref(null);

const addTodo = () => {
  if (newTodoTitle.value && editItemId.value) {
    const editedIndex = items.value.findIndex(
      (item) => item.id === editItemId.value
    );
    if (editedIndex !== -1) {
      items.value[editedIndex].title = newTodoTitle.value;
      items.value[editedIndex].createdAt = new Date().toISOString();
      newTodoTitle.value = "";
      editItemId.value = null;
    }
  } else {
    items.value.push({
      id: Math.floor(Math.random() * 1000),
      title: newTodoTitle.value,
      createdAt: new Date().toISOString(),
    });
    newTodoTitle.value = "";
  }
};

const deleteTodo = (id) => {
  items.value = items.value.filter((item) => item.id !== id);
};

const editTodo = (id) => {
  editItemId.value = id;
  const item = items.value.find((item) => item.id === id);
  if (item) {
    newTodoTitle.value = item.title;
  }
};

const sortByCreationDate = () => {
  items.value.sort((a, b) => new Date(a.createdAt) - new Date(b.createdAt));
};

const sortById = () => {
  items.value.sort((a, b) => a.id - b.id);
};
</script>

<template>
  <div class="mb-2" v-auto-animate>
    <input
      type="text"
      name="title"
      v-model="newTodoTitle"
      placeholder="Test Megafon todolist vue 3 Tailwind Css"
      class="border-solid border-2 border-slate-500"
    />
    <button
      @click="addTodo"
      class="px-4 border-solid border-2 border-slate-500"
      v-auto-animate
    >
      Submit
    </button>
  </div>
  <button
    class="px-4 mb-4 border-solid border-2 border-slate-500"
    @click="sortByCreationDate"
  >
    Sort by Creation Date
  </button>
  <button
    class="px-4 mb-4 border-solid border-2 border-slate-500"
    @click="sortById"
  >
    Sort by ID
  </button>
  <div class="w-4/5 m-auto" v-auto-animate>
    <table className="w-[80%] m-auto" v-auto-animate>
      <thead className="border-solid border-2 border-slate-500 p-2">
        <tr className="border-solid border-2  border-slate-500 p-2   ">
          <th className="border-solid border-2 border-slate-500 p-2">id</th>
          <th className="border-solid border-2 border-slate-500 p-2">Date</th>
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
            {{ item.createdAt }}
          </td>
          <td class="border-solid border-2 border-slate-500 p-2">
            {{ item.id === editItemId ? newTodoTitle : item.title }}
          </td>
          <td
            class="border-solid border-2 border-slate-500 p-2"
            @click="deleteTodo(item.id)"
          >
            Del
          </td>
          <td
            class="border-solid border-2 border-slate-500 p-2"
            @click="editTodo(item.id)"
            v-auto-animate
          >
            Edit
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
