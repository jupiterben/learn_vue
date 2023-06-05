<template>
  <div>
    <form @submit.prevent="addTask">
      <span>新建 {{ totalCount }}</span>
      <input v-model="inputText" placheolder="输入任务..." />
      <button>添加</button>
    </form>
    <ol>
      <li v-for="(item, index) in todos">
        {{ `${item} ${index}` }}
        <button @click="removeTask(index)">删除</button>
        <hr />
      </li>
    </ol>
  </div>
</template>

<script setup lang="ts">
import { computed, reactive, ref } from "vue";

const inputText = reactive(ref(""));
const todos: string[] = reactive([]);

const totalCount = computed(() => {
  return todos.length;
});

const addTask = () => {
  if (inputText) {
    todos.push(inputText.value);
    inputText.value = "";
  }
};
const removeTask = (index: number) => {
  todos.splice(index, 1);
};
</script>
