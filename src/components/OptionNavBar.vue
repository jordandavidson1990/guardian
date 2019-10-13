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
        {name: 'news', color: 'red'},
        {name: 'opinion', color: 'orange'},
        {name: 'sport', color: 'blue'},
        {name: 'culture', color: 'tan'},
        {name: 'lifestyle', color: 'pink'}
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
  border-top: 1px solid white;

}
</style>
