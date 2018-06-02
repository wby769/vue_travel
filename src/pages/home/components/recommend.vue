<template>
  <div class="recommend">
    <div class="recommend-title border-bottom">热销推荐</div>
    <router-link tag="div" :to="'/detail/' + item.id" class="recommend-list border-bottom" v-for="item of list" :key="item.id">
      <img class="recommend-list-img" v-lazy="item.imgUrl">
      <div class="recommend-info">
        <h1 class="recommend-list-title">{{item.title}}</h1>
        <p class="recommend-list-desc">{{item.desc}}</p>
        <button href="#" class="recommend-list-btn">查看详情</button>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/mixin.styl"
  .recommend
    border-bottom: .24rem solid #eee
    .recommend-title
      font-size: .32rem
      line-height: .64rem
      padding-left: .2rem
    .recommend-list
      display: flex
      height:2rem
      .recommend-list-img
        width: 1.8rem
        height: 1.8rem
        margin: .1rem
      .recommend-info
        flex: 1
        min-width: 0
        .recommend-list-title
          font-size: .36rem
          margin-top: .14rem
          ellipsis()
        .recommend-list-desc
          font-size: .28rem
          color: #999
          margin-top: .1rem
          line-height: .34rem
        .recommend-list-btn
          background: #ffa500
          color: #fff
          padding: 0.04rem .1rem
          position: absolute
          bottom: .1rem
</style>
