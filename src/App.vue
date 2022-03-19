<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <input class="text" type="text" v-model="b">  
    <maintest :ainto="a" :binto="b" @update="updateinfo"></maintest>
  </div>
</template>

<script>
import maintest from '@/components/MainTest.vue';

export default {
  name: 'App',
  components: {
    maintest,
  },
  data(){
    return{
      a: '輸入list',
      b: null,
    }
  },
  methods:{
    updateinfo(){
      this.b = '';
    },
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.text{
  display: block;
  margin: auto;
}
</style>
