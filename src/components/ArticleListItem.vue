<template lang="html">
  <div v-if="article" class="item">
    <li v-on:click="showContent" >{{article.webTitle}}</li>
    <div v-if="!isHidden">
      <p>{{article.pillarName}}</p>
      <a :href="article.webUrl">{{article.webTitle}}</a>
    </div>
  </div>
</template>

<script>
export default {
  name:'article-list-item',
  props:['article'],
  data(){
    return{
      isHidden: true
    }
  },
  methods:{
    showContent: function(){
      if (this.isHidden) {
        this.isHidden = false
      }else{
        this.isHidden = true
      }
      // this.isHidden ? this.isHidden = true : this.isHidden = false
    }
  }
}
</script>

<style lang="css" scoped>
li{
  background-color: palegoldenrod;
  border: 1px solid black;
  cursor:pointer;
  display: flex;
  width: 36vw;
  height: auto;
}

/* z-index: 200;
position: fixed */
</style>
