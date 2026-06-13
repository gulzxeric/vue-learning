<script setup>
import { ref } from 'vue'

const isVisible = ref(true)

const items = ref(['苹果', '香蕉', '橙子'])
const selectedId = ref(null)
const newsToggle = ref(false)
const todoItem = ref(null)
const news = ref([
  { id: 1, title: 'Vue 3.5 发布', date: '2026-01-15', category: '技术' },
  { id: 2, title: 'Node.js 22 发布', date: '2026-01-14', category: '技术' },
  { id: 3, title: 'AI 新突破', date: '2026-01-13', category: '科技' },
])

const todos = ref(['eat', 'sleep', 'learn vue'])


function toggle() {
  isVisible.value = !isVisible.value
}

function selectNews(id) {
  selectedId.value = (selectedId.value === id) ? null : id
}

function addItem() {
  if (todoItem.value) {
    todos.value.push(todoItem.value)
    todoItem.value = ''
  }
}

const doneStates = ref([false, false, false])

function toggleDone(index) {
  doneStates.value[index] = !doneStates.value[index]
}
</script>
<template>
  <button @click="toggle">切换显示</button>
  <p v-if='isVisible'>我是显示的</p>
  <p v-else>我不显示</p>
  <p v-show="isVisible">我也显示</p>
  <ul>
    <li v-for="(item, index) in items" :key='index'>{{ index }}.{{ item }}</li>
  </ul>
  <ul>
    <li v-for="{ id, title, date, category } in news" :key='id'>{{ title }} {{ date }}<span v-if="selectedId === id">{{
      category }} </span> <button @click='selectNews(id)'>{{ selectedId === id ? 'Hide' : 'Display' }}
        category</button></li>
  </ul>
  <ul>
    <p>待办事项清单</p>
    <button @click='addItem'>新增待办事项</button><input v-model="todoItem" placeholder="Please enter new task">
    <li v-for="(item, index) in todos" :key="index">
      <span :style="{ textDecoration: doneStates[index] ? 'line-through' : 'none' }">{{ item }}</span>
      <button @click="toggleDone(index)">{{ doneStates[index] ? '取消划线' : '划线' }}</button>
    </li>
  </ul>
</template>