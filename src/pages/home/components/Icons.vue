<template>
  <div class="icons">
    <swiper class="icons-box" :options="swiperOption">
      <swiper-slide class="icons-list-box" v-for="(page,index) of pages" :key="index">
        <div class="icons-list" v-for="item of page" :key="item.id">
          <img class="icons-img" :src="item.imgUrl">
          <p class="icons-title">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixin.styl'
  .icons >>> .swiper-pagination-bullet-active
    background: $bgColor
    opacity: 1
  .icons >>> .swiper-pagination-bullets
    bottom: 5px
  .icons
    padding-top: .1rem
    border-bottom: .24rem solid #eee
    .icons-box
      width: 100%
      height: 0
      padding-bottom: 56%
      overflow: hidden
      .icons-list-box
        display: flex
        flex-wrap: wrap
        .icons-list
          width: 25%
          height: 0
          padding-bottom: 25%
          text-align: center
          .icons-img
            width: 60%
            display: block
            margin: 0.1rem auto 0.2rem
          .icons-title
            font-size: .24rem
            ellipsis()
</style>
