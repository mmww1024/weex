<template>
  <div class="wrapper">
    <div class="master">
      <header :newsInfo="newsInfo"></header>
      <content :contentList="contentList"></content>
    </div>
    <div class="reply">
      <related :recommendList="recommendList"></related>
      <hot-reviews :topComment="topComment"></hot-reviews>
      <latest-reviews :newComment="newComment"></latest-reviews>
    </div>
  </div>
</template>

<style lang="sass" src="../assets/sass/index.scss"></style>

<script>
  import axios from 'axios';
  import _ from 'lodash';
  import header from './news/header.vue';
  import content from './news/content.vue';
  import related from './news/related.vue';
  import hotReviews from './news/hotReviews.vue';
  import latestReviews from './news/latestReviews.vue';
  export default {
    components:{
      header,content,related,hotReviews,latestReviews
      },
    created:function(){
      this.init();
    },
    data: function(){
      return {
        newsInfo:{},
        contentList:[],
        recommendList:[],
        topComment:[],
        newComment:[]
      };
    },
    methods: {
      init: function (e) {
        var that = this;
        axios.get('../src/data/detail.json')
          .then(function (response) {
            // var res = JSON.parse(response);
            if(response.data.status){
              that.resdata = response.data.data;
              that.newsInfo = that.deepClone(that.resdata.newsInfo);
              that.contentList = that.deepClone(that.resdata.contentList);
              that.recommendList = that.deepClone(that.resdata.recommendList);
              that.topComment = that.deepClone(that.resdata.topComment);
              that.newComment = that.deepClone(that.resdata.newComment);
              console.log(that.resdata)
              console.log(that.topComment)
            }

            // console.log(response);
          })
          .catch(function (error) {
            console.log(error);
          });

      },
      deepClone: function(data) {
        let newObj = _.isArray(data) ? [] : ( _.isObject(data) ? {} : data);
        if (data instanceof Object) {
          for (let key in data) {
            newObj[key] = this.deepClone(data[key]);
          }
        }

        return newObj;
      }
    }
  }
</script>
