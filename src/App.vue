<template lang="html">
  <div class="">
  <guardian-header class="header" :topic="topic"></guardian-header>
  <search-bar ></search-bar>
  <h3>Topic: {{topic}}</h3>
  <articles-list :articles="newsArticles"> </articles-list>
</div>

</template>

<script>
import ArticlesList from './components/ArticlesList.vue'
import GuardianHeader from './components/GuardianHeader.vue'
import SearchBar from './components/SearchBar.vue'
export default {
  name:'app',
  data(){
    return{
      topic: 'brexit',
      newsArticles: []
    }
  },
  mounted(){
    this.gatherData()
  },
  methods:{
    gatherData: function(){
      fetch(`https://content.guardianapis.com/search?q=${this.topic}&format=json&api-key=1dffd669-7e31-474d-8345-b740946075cb`)
      .then(res => res.json())
      .then(data => this.newsArticles = data.response.results)
    }
  },
  components:{
    "articles-list":ArticlesList,
    "guardian-header":GuardianHeader,
    "search-bar":SearchBar
  }
}
</script>

<style lang="css" scoped>
@font-face {
  font-family: "guardian";
  src: url('/assets/fonts/Vogue.ttf')  format('embedded-opentype');
}
*{
  margin: 0;
  padding: 0;
}
.header{
  margin:0;
  width:100%;
  background-color: #052962;
}
</style>
