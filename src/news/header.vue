<template>
  <div>
    <div class="title">
        <p class="master-title" id="mytitle">{{newsInfo.title}}</p>
    </div>
    <div class="news-check">
       <div class="news-check-name">
           <span class="editor">{{newsInfo.author}}</span>
       </div>
       <span>{{newsInfo.time}}</span>
   </div>
 </div>
</template>

// <style lang="sass" src="../../assets/sass/news/_header.scss"></style>

<script>
  export default {
    props:['newsInfo'],
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
