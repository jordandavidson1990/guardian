<template lang="html">
  <div class="">
    <select v-if="searchTopics" v-model="selectedTopic" v-on:change="handleChange">
      <option disabled value="Choose a Topic...">choose a topic...</option>
      <option :value="topic.id" v-for="topic in searchTopics">{{topic.id}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name:'search-bar',
  data(){
    return{
      searchTopics:[],
      selectedTopic:""
    }
  },
  mounted(){
    this.getTopics()
  },
  methods:{
    getTopics: function(){
      fetch('https://content.guardianapis.com/sections?api-key=test')
      .then(res => res.json())
      .then(data => this.searchTopics = data.response.results)
    },
    handleChange: function(){
      eventBus.$emit('topic-selected', this.selectedTopic)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
