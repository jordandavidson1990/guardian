<template lang="html">
  <div class="">
    <ul>
      <article-list-item v-for="(article, index) in articles" :key="index" :article="article"></article-list-item>
    </ul>
  </div>
</template>

<script>
import ArticleListItem from './ArticleListItem.vue'

export default {
  name:'articles-list',
  props:['articles'],
  components:{
    "article-list-item":ArticleListItem
  }
}
</script>

<style lang="css" scoped>
ul{
  /* display: flex; */
  flex-flow: row wrap;
}
</style>
