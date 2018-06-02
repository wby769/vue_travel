<template>
  <div class="header">
    <div class="header-left">
      <i class="iconfont icon-back"></i>
    </div>
    <div class="header-inp">
      <i class="iconfont icon-sousuo"></i>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        <span class="header-city">{{this.city}}</span>
        <i class="iconfont icon-down"></i>
      </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixin.styl'
  .header
    display: flex
    line-height: .88rem
    background: $bgColor
    color: #fff
    .header-left
      width: .8rem
      float: left
      .icon-back
        font-size: .4rem
        margin-left: .16rem
    .header-inp
      flex: 1
      background: #fff
      border-radius: .1rem
      margin-top: .12rem
      height: .64rem
      line-height: .64rem
      color: #ccc
      .icon-sousuo
        font-size: .38rem
        margin-left: 0.1rem
        vertical-align: middle
    .header-right
      min-width: 1.3rem
      float: right
      text-align: center
      color: #fff
      .header-city
        display: inline-block
        max-width: 1.12rem
        vertical-align: middle
        margin-left: .1rem
        ellipsis()
      .icon-down
        position: relative
        left: -.03rem
        font-size: .24rem
</style>
