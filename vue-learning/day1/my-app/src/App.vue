<script setup>
import { ref } from 'vue'

const myColor = ref({ color: 'red' })
const base = ref({ color: 'blue', fontSize: '20px' })
const extra = ref({ fontWeight: 'bold' })
const isActive = ref(true)
const classA = ref('green-text')
const classB = ref('bold-text')

const rawHtml = '<strong>加粗文字</strong>'


const linkUrl = ref('https://vuejs.org')
const imageSrc = ref('https://avatars.githubusercontent.com/u/190572129?v=4&size=64')
const imageDesc = ref('示例图片')
const isDisabled = ref(false)

const items = ref(['A', 'B', 'C'])
function shuffle() {
  items.value = ['B', 'C', 'A']
}

function lstDelete(index) {
  items.value.splice(index, 1)
}
</script>
<style scoped>
.active {
  color: red;
  font-weight: bold;
}

.green-text {
  color: green;
}

.bold-text {
  font-weight: lighter;
}
</style>


<template>
  <button :style='myColor'>你好</button>
  <div :style="[base, extra]">这是合并样式</div>
  <p :class="[{ active: isActive }, classA, classB]">这句话可以变红</p>
  <p>{{ rawHtml }}</p>
  <p v-html='rawHtml'></p>

  <a :href="linkUrl">点我</a>
  <img :src="imageSrc" :alt="imageDesc">
  <button :disabled="isDisabled">不能点</button>

  <button @click="shuffle">打乱顺序</button>
  <ul>
    <!-- <li v-for="(item, index) in items" :key="item">{{ item }}</li> -->
    <li v-for="(item, index) in items" :key="item">
      <input placeholder="输入点什么">
      <button @click='lstDelete(index)'>删除</button>
      {{ item }}
    </li>
  </ul>

</template>