<template>
  <div class="master-content">
      <div v-for="(item, i) in contentList" :page="i"> {{ item.content }} </div>
  </div>
</template>

<style>
</style>

<script>
  export default {
    props:['contentList'],
    data: function(){
      return {};
    },
    methods: {
      update: function (e) {
        this.target = 'Weex'
        console.log('target:', this.target)
      }
    }
  }
</script>
