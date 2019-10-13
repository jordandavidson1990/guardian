<template lang="html">
  <p>{{date}}</p>
</template>

<script>
export default {
  name: 'date-now',
  computed:{
    date: function(){
      var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
      var today  = new Date();
      return today.toLocaleDateString("en-US", options);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
