<template>
  <div v-if="topComment[0]" class="hot-reply recommend-mode">
    <h2 class="title"><i class="icon icon-hotComment">n</i>热门评论</h2>
    <ul>
        <li v-for="(item, i) in topComment" :id="item.commentId" :userid="item.userId" :username="item.userName" :key="i">
          <div class="reply-li-wrap">
              <div class="avatar  ">
                  <div class="avatar-photo  crowded">
                      <a href="" class="level">
                          <div class="face-wrap lazy">
                              <image class="tx" :src="item.icon" style="width:35px;height:35px"></image>
                          </div>
                          <span v-if="item.is_vip" class="authen"></span>
                      </a>
                      <div class="avatar-name">
                          <a href=""><text class="master-name">{{ item.userName }}</text></a>
                          <p class="master-time">{{ item.time }}</p>
                      </div>
                  </div>
                  <div class="avatar-operate">
                      <div class="avatar-operate-thumb"><a href="javascript:;" ><text class="icon icon-praise">{{ item.isSupport?'3':'2' }}</text></a>
                      <text class="praiseCount" :praisecount="item.praiseCount">{{ item.praiseCount > 9999 ? parseFloat((tiem.praiseCount/10000).toFixed(1)) + '万' : item.praiseCount }}</text>
                      </div>
                      <a href="javascript:;" class="avatar-operate-reply usual"><text class="icon icon-comment1">d</text></a>
                  </div>
              </div>
              <div class="reply-content">
                  <text class="reply-userContent">{{ item.content }}</text>
                  <div v-for="(item,i) in item.layoutList" class="reply-re-content" :key="i">
                      <div class="avatar crowded">
                        <text class="username">{{ item.userName }}</text>
                        <text class="floorname">{{ item.floorName }}</text>
                      </div>
                      <text>{{ item.content }}</text>
                  </div>

                  <div v-if="item.imageUrl" class="insert-img">
                      <image src="item.imageUrl" style="width:100%;height:auto;"></image>
                  </div>
              </div>
          </div>
        </li>
    </ul>
</div>
</template>

<style>
</style>

<script>
export default {
  props:['topComment'],
  data: function(){
    return {

    };
  },
  methods: {
    update: function (e) {
      this.target = 'Weex'
      console.log('target:', this.target)
    }
  }
}
</script>
