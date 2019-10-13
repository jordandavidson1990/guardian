<template lang="html">
  <div class="">
    <guardian-header class="header" :topic="topic"></guardian-header>
    <option-nav-bar></option-nav-bar>
    <div class="container">
      <date-now></date-now>
      <div class="search">
        <h3>{{topic}}</h3>
        <search-bar ></search-bar>
      </div>
      <articles-list :articles="newsArticles"> </articles-list>
    </div>
  </div>

</template>

<script>
import OptionNavBar from './components/OptionNavBar.vue'
import ArticlesList from './components/ArticlesList.vue'
import GuardianHeader from './components/GuardianHeader.vue'
import SearchBar from './components/SearchBar.vue'
import DateNow from './components/DateNow.vue'
import {eventBus} from './main.js'
export default {
  name:'app',
  data(){
    return{
      topic: 'brexit',
      newsArticles: [],

    }
  },
  mounted(){
    this.gatherData()

    eventBus.$on('topic-selected', (topic) => {
      fetch(`https://content.guardianapis.com/search?q=${topic}&format=json&api-key=1dffd669-7e31-474d-8345-b740946075cb`)
        .then(res => res.json())
        .then(data => this.newsArticles = data.response.results)
        this.topic = topic
      })
    },
    computed:{
      getTopic: function(){
        return this.topic
      }
    },
    methods:{
      gatherData: function(){
        fetch(`https://content.guardianapis.com/search?q=${this.getTopic}&format=json&api-key=1dffd669-7e31-474d-8345-b740946075cb`)
          .then(res => res.json())
          .then(data => this.newsArticles = data.response.results)
        }
      },
      components:{
        "articles-list":ArticlesList,
        "guardian-header":GuardianHeader,
        "search-bar":SearchBar,
        "option-nav-bar":OptionNavBar,
        "date-now":DateNow
      }
    }
    </script>

    <style lang="css" scoped>

    .search{
      display: flex;
      justify-content: space-between;
    }
    @font-face {
      font-family: "guardian";
      src: url('/assets/fonts/Vogue.ttf')  format('embedded-opentype');
    }
    h3{
      font-family: "guardian";
      color: #C70000;
      margin-left: 3vw;
      font-size: 8vw;
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
