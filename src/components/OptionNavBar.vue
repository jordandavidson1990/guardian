<template lang="html">
  <div class="">
    <ul>
      <option-item v-for="(option, index) in mainOptions" :option="option" :key="index"></option-item>
    </ul>
  </div>
</template>

<script>
import OptionItem from './OptionItem.vue'

export default {
  name:'option-nav-bar',
  data(){
    return{
      mainOptions:[
        {name: 'news', color: '#C70000'},
        {name: 'opinion', color: '#ff7f0f'},
        {name: 'sport', color: '#00b2ff'},
        {name: 'culture', color: '#eacca0'},
        {name: 'lifestyle', color: '#ffabdb'}
      ]
    }
  },
  components:{
    "option-item":OptionItem
  }
}
</script>

<style lang="css" scoped>
ul{
  display:flex;
  justify-content: space-evenly;
  background-color: #052962;
  padding-bottom: 2vh;
}
</style>
