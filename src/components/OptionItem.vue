<template lang="html">
  <h5 @click="handleClick">{{option.name}}</h5>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'option-item',
  props:['option'],
  methods:{
    handleClick: function(){
      eventBus.$emit('topic-selected', this.option.name)
    }
  }
}
</script>

<style lang="css" scoped>
h5{
  margin-top: 2vh;
  border-top: 1px solid white;
  border-left: 1px solid white;
  border-right: 1px solid white;
  width: auto;
  padding: 2px;
  color: white;
  font-size: 4vw;
  cursor: pointer;


}
h5:hover{
  border-top: 1px solid grey;
  border-left: 1px solid inherit;
  border-right: 1px solid inherit;
  /* background:grey; */
}
</style>
