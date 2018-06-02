<template>
  <div class="loading">
    <div class="loading-main">
      <img class="loading-img" src="@/assets/images/loading.gif">
      <p>{{this.title}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonLoading',
  props: {
    title: {
      type: String,
      default: '正在载入中...'
    }
  }
}
</script>

<style lang="stylus" scoped>
  .loading
    position: fixed
    top: 0
    bottom: 0
    left: 0
    right: 0
    z-index: 8
    background: #fff
    text-align: center
    color: #999
    .loading-main
      position: absolute
      top: 50%
      width: 100%
      transform: translate(0,-50%)
      .loading-img
        width: 3rem
</style>
