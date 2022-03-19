<template>
  <div class="mainmest">
    <p>{{ ainto }}</p>
    <button @click="add(binto)">add item</button>
    <button @click="deleteall">deleteall</button>
    <ul>
      <li class="arraybox" v-for="item in box" :key="item.id">
        <p :class="{ active:item.status }" class="tex" v-if="item.modify" @click="markup(item)">{{ item.name }}</p>
        <input v-else type="text" class="intotext" v-model.trim="item.name">
        <button @click="modifyitem(item)">modify</button> 
        <button @click="deleteitem(item)">delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'MainTest',
  props:{
    ainto:{},
    binto:{},
  },
  data(){
    return{
      box:[],
      b: '',
      modifytxt: '',
    }
  },
  methods:{
    add(binto){
      let time = Date.now();
      this.box.push({name:binto, id:time, status:false, modify:true});
    },
    markup(item){
      item.status = !item.status; 
    },
    deleteitem(sub){
      let vm = this;
      vm.box.forEach(function(item, index){
        if(item.id === sub.id){
          vm.box.splice(index, 1);
        }
      })
    },
    deleteall(){
      let vm = this;
      vm.box = [];
    },
    modifyitem(item){
      item.modify = !item.modify;
    }
  },
  watch:{
    box:{
      deep: true,
      handler(){
        this.$emit('update');
      },
    }
  },
}
</script>

<style>
  .box{
    margin: 10px;
  }
  .tex.active{
    text-decoration:line-through;
  }
  .tex{
    display: inline-block;
    margin: 0 10px;
  }
</style>