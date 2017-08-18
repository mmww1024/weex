<template>
  <div v-if="recommendList[0]" class="recommend-mode">
      <h2 class="title"><i class="icon icon-relateRec">a</i>相关推荐</h2>
      <a v-for="(item, i) in recommendList" :key="i" href="" class="recommend-list">
          <div class="left">
              <span class="name">{{ item.title }}</span>
                  <em v-if="item.label" class="tag">{{ item.label }}</em>
                  <div v-else-if="item.commentCount" class="time-recom">
                      <span class="time">
                      {{ item.commentCount > 9999 ? parseFloat((item.commentCount/10000).toFixed(1)) + '万' : item.commentCount }}
                      评论</span>
                      <span class="recom">{{ item.putTime }}</span>
                  </div>
          </div>
          <div class="right lazy" :original="item.imageUrl">
              <image :src="item.imageUrl" style="width: 109px;height: 73px;"></image>
          </div>
      </a>
  </div>
</template>

<style>
</style>

<script>
export default {
  props:['recommendList'],
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
