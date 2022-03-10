<template>
  <ul>
    <li v-for="(num, i) in 10" :key="i">{{ num }}-{{ i }}</li>
  </ul>
  <ol>
    <li v-for="(item, i) in num1" :key="item.id">{{ item.title }}-{{ i }}</li>
  </ol>
  <ol>
    <li v-for="(item, key, i) in person" :key="item.id">{{ item }}-{{ key }}-{{i}}</li>
  </ol>
  <h1 @click="count++">{{ count }}</h1>
  <button @click="handleEvent(10, $event)">event</button>
  <!-- 处理多个函数 -->
  <div :style="{background: color}">change style</div>
  <button @click="handleEvent(10),changleColor($event)">处理多个函数</button>
  <!-- once修饰符, 事件只会触发一次 -->
  <button @click.once="count++">once修饰符{{ count }}</button>
  <!-- 按键修饰符 -->
  <input type="text" @keydown.enter="handleEnter('enter', $event)">
</template>
<script>
export default {
  data() {
    return {
      num1: [{
        title: 't1',
        id: 0,
      }, {
        title: 't2',
        id: 1,
      }],
      person: {
        name: 'cs',
        age: 30,
        feature: '篮球',
      },
      count: 0,
      color: 'red',
    }
  },
  methods: {
    handleEvent(num) {
      this.count+=num
    },
    changleColor(event) {
      console.log(event)
      this.color = 'purple'
    },
    handleEnter(action, e) {
      console.log(action, e)
    },
  },

</script>

<style scoped>

</style>>
