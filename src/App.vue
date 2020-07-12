<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
    <h2> {{text}}</h2>
    <h2>{{texting}}</h2>
    <button @click="btnTest">测试按钮</button>
  </div>
</template>

<script lang='ts'>
import { Vue, Component, Watch} from 'vue-property-decorator'

@Component
export default class App extends Vue {
  private text:string = '' // 定义一个变量 同原data中数据
  private obj:Object = {
    a: 1,
    b: 2
  }
  // 计算属性
  private get texting () {
    return this.text + ' is commputed'
  }
  // 监听
  @Watch('text')
  watchText ():void { // 监听函数 命名任意
    console.log('text值改变了')
  }
  @Watch('obj', {deep:true}) // 深度监听
  watchObj ():void {
    console.log('obj改变了')
  }
  created ():void {
    this.text = 'hello typescript'
    // this.obj.a 报错
    this.obj['a']= 3
  }
  // method
  btnTest () {
    console.log('我是测试按钮')
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
