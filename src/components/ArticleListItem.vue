<template lang="html">
  <div v-if="article" class="item">
    <div v-if="!isHidden" class="list-item">
      <a :href="article.webUrl">{{article.webTitle}}</a>
    </div>
    <li v-on:click="showContent" >{{article.webTitle}}</li>
  </div>
</template>

<script>
export default {
  name:'article-list-item',
  props:['article'],
  data(){
    return{
      isHidden: true,
      phrase:""
    }
  },
  methods:{
    showContent: function(){
      if (this.isHidden) {
        this.isHidden = false
      }else{
        this.isHidden = true
      }
    }
  }
}
</script>

<style lang="css" scoped>
li, .list-item{
  border: 0.5px solid black;
  cursor:pointer;
  display: flex;
}
li{
  background-color: #C7DBE6;
  border-top: 1px #C70000 solid;
  margin-top: 1vh;
  font-family: "guardian";
  width:25vw;
  height: 40vh;
  display: flex;
  align-items: center;
  text-align: center;
}

.list-item{
  background-color: #C7DBE6;
  z-index: 0;
  margin-top: 1vh;
  position: absolute;
}
a:link {
  text-decoration: none;
}


</style>
