<template>
  <div id="app">
    <img src="./assets/logo.png">
    <Tree :data="data" @checkEvent="getEvent" checkBox></Tree>
    <i class="fa fa-camera-retro fa-5x"></i>
  </div>
</template>

<script>
  import {Tree} from './components/tree/tree.js'
  export default {
    name: 'app',
    data(){
      return {
        data: [
          {
            label: '一级1',
            id: '',
            class: '',
            style: '',
            uid: '野马汽车1',
            children: [{label: '11',uid: '野马汽车2',children: [{label: '111'}]},{label: '12',uid: '野马汽车3',children: [{label: '121',uid: 'T70-80'}]},{label: '13',uid: '野马汽车4'}]
          },
          {
            label: '一级2',
            children: [{label: '21'},{label: '22'},{label: '23'}]
          },
          {
            label: '一级3',
            children: [{label: '31'},{label: '32'},{label: '33'}]
          },
        ],
        childEvent: {}
      }
    },
    components: { Tree },
    methods: {
      getEvent (getEvent) {
        this.childEvent = getEvent;
        console.log(this.childEvent)
      }
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
