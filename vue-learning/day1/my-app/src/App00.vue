<script setup>
import { ref } from 'vue'

const count = ref(0)
const step = ref(1)

function increment() {
  count.value += step.value
}
</script>

<template>
  <div>
    <h1>计数器</h1>
    <p>你点击了 {{ count }} 次</p>
    <button @click="increment">点击 + {{ step }}</button>
    <button @click="count = 0">Reset</button>
    <input type="number" v-model.number="step" placeholder="设置步长">
  </div>
</template>

<style scoped></style>