<template>
  <div>
    <div class="item"  v-for="(item, index) of list" :key="index">
      <div class="item-list border-bottom">
        <span class="title-img"></span>
        {{item.title}}
      </div>
      <div v-if="item.children">
        <detail-list :list="item.children" class="item-children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .item-list
    line-height: .6rem
    font-size: .28rem
    .title-img
      position: relative
      top: .08rem
      left: .1rem
      display: inline-block
      width: .36rem
      height: .36rem
      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
      margin-right: .1rem
      background-size: .4rem 3rem
  .item-children
    padding-left: .2rem
</style>
