<template>
  <div class="weekend">
    <div class="weekend-title border-bottom">周末游玩</div>
    <ul>
      <li class="weekend-list" v-for="item of list" :key="item.id">
        <div class="weekend-img">
          <img class="weekend-list-img" v-lazy="item.imgUrl">
        </div>
        <h1 class="weekend-list-title">{{item.title}}</h1>
        <p class="weekend-list-desc">{{item.desc}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixin.styl'
  .weekend
    border-bottom: .24rem solid #eee
    .weekend-title
      font-size: .32rem
      line-height: .64rem
      padding-left: .2rem
    .weekend-list
      border-bottom: .1rem solid #f8f8f8
      &:last-child
        border-bottom: none
      .weekend-img
        overflow: hidden
        width: 100%
        height: 0
        padding-bottom: 37%
        .weekend-list-img
          width: 100%
      .weekend-list-title
        font-size: .32rem
        margin: .1rem 0 0 .1rem
        ellipsis()
      .weekend-list-desc
        font-size: .28rem
        color: #999
        margin: .1rem 0 .2rem .1rem
        ellipsis()
</style>
