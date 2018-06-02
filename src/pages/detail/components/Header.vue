<template>
  <div>
    <div @click="$router.go(-1)" class="header-abs" v-show="showAbs">
      <i class="iconfont icon-back"></i>
    </div>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      <router-link to="/">
        <i class="iconfont icon-back"></i>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header-abs
    position: absolute
    left: .2rem
    top: .2rem
    width: .7rem
    height: .7rem
    border-radius: 50%
    background: rgba(0, 0, 0, 0.6)
    color: #fff
    text-align: center
    line-height: .7rem
    .icon-back
      font-size: .4rem
  .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    line-height: .88rem
    background: $bgColor
    text-align: center
    color: #fff
    font-size: .32rem
    z-index: 2
    .icon-back
      position: absolute
      left: 0
      top: 0
      padding: 0 .2rem
      font-size: .4rem
      color: #fff
</style>
