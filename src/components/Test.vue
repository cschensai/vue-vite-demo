<template>
  <h2>{{ msg }}</h2>
  <!-- 一次渲染，后面再不会发生改变 -->
  <span @click="changeMsg" v-once>
    {{ msg }}
  </span>
  <!-- v-model v-once -->
  <input type="text" v-model="msg">
  <!-- v-html -->
  <div v-html="content"></div>
  <!-- 动态指令 -->
  <h2 @[eventName]="attrName = attrName === 'class' ? 'id' : 'class'">改变背景颜色</h2>
  <h3 :[attrName]="d1"></h3>
  <!-- 计算属性 -->
  <h4>{{ reverseMsg }}</h4>
  <!-- 数据监听属性 -->
  <input type="text" v-model="watchMsg" />
  <h4>{{ watchMsg }}</h4>
  <!-- 动态class -->
  <h4 :class="{normal: true, active: isActive}">动态class</h4>
  <button @click="isActive=!isActive">切换class</button>
  <h4 :class="classArr">classArr</h4>
  <button @click="classArr.pop()">切换class</button>
  <h4 :class="['normal', { active: isActive }]">arr and object</h4>
  <button @click="isActive=!isActive">切换class</button>
  <!-- 内联样式 -->
  <div style="background: orange">inline style0</div>
  <div :style="styleStr">inline style1</div>
  <div :style="{background: 'purple'}">inline style2</div>
  <div :style="styleObj">inline style3</div>
  <div :style="[styleObj, { width: '200px', margin: '0 auto' }]">inline style4</div>
  <button @click="changeStyle">切换style</button>
  <!-- 条件渲染 -->
  <div v-if="ifTrue">vif true</div>
  <div v-else>vif false</div>
  <button @click="ifTrue = !ifTrue">v-if</button>
  <div v-show="show">vshow true</div>
  <button @click="show = !show">v-show</button>
</template>

<script>
export default {
  data() {
    return {
      msg: 'hello',
      content: '<i>html text</i>',
      eventName: 'click',
      attrName: 'class',
      d1: 'd1',
      watchMsg: 'watchMsg',
      isActive: false,
      classArr: ['normal', 'active'],
      styleStr: 'background: yellow',
      styleObj: {
        backgroundColor: 'pink',
        border: '1px solid red',
      },
      ifTrue: true,
      show: true
    }
  },
  methods: {
    changeMsg() {
      this.msg = 'my hello'
    },
    changeStyle() {
      this.styleObj.backgroundColor = 'green';
    }
  },
  computed: {
    reverseMsg() {
      return this.msg.split('').reverse().join('');
    }
  },
  watch: {
    // 观察模式
    watchMsg(newVal, oldVal) {
      console.log(newVal, oldVal)
      if (newVal.length < 10) {
        console.log(`输入的值长度太少${newVal}`)
      }
    },
  },
}
</script>

<style scoped>
#d1 {
  margin: 0 auto;
  width: 100px;
  height: 100px;
  background-color: red;
}
.d1 {
  margin: 0 auto;
  width: 100px;
  height: 100px;
  background-color: green;
}
.normal {
  background-color: red;
}
.active {
  background-color: green;
}
</style>
