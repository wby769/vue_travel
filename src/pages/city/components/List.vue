<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="main">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-box">
            <div class="button-city">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="main">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-box" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
            <div class="button-city">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="main" v-for="(item, key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.scroll.scrollTo(0, 0)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  activated () {
    this.scroll.scrollTo(0, 0)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .border-topbottom
    &:before
      border-color: #ccc
    &:after
      border-color: #ccc
  .list
    overflow: hidden
    position: absolute
    top: 1.6rem
    left: 0
    right: 0
    bottom: 0
    .title
      height: .48rem
      line-height: .48rem
      padding-left: .16rem
      font-size: .28rem
      background: #f5f5f5
      color: #666
    .button-list
      overflow: hidden
      padding: .1rem .6rem .1rem .1rem
      .button-box
        float: left
        width: 33.3%
        .button-city
          margin: .1rem
          padding: .1rem 0
          text-align: center
          border: 1px solid #ccc
          border-radius: .06rem
    .item
      line-height: .6rem
      padding-left: .2rem
</style>
