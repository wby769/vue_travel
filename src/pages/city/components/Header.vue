<template>
  <div>
    <div class="header">
      <router-link to="/">
        <i class="iconfont icon-back"></i>
      </router-link>
      城市选择
    </div>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    position: relative
    line-height: .88rem
    text-align: center
    font-size: .32rem
    color: #fff
    background: $bgColor
    .icon-back
      position: absolute
      font-size: .4rem
      left: 0
      padding: 0 .2rem
      color: #fff
</style>
