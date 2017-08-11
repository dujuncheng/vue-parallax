<template>
  <div id="app">
    <imgcontainer :bgimg="'1.jpg'" :title="'标题一'" :index="'0'" :leaveTitleIndex="leaveTitleIndex" :leaveTitleTop="leaveTitleTop" :scrollY="scrollY"></imgcontainer>
    <imgcontainer :bgimg="'2.jpg'" :title="'标题二'" :index="'1'" :leaveTitleIndex="leaveTitleIndex" :leaveTitleTop="leaveTitleTop" :scrollY="scrollY"></imgcontainer>
    <imgcontainer :bgimg="'3.jpg'" :title="'标题三'" :index="'2'" :leaveTitleIndex="leaveTitleIndex" :leaveTitleTop="leaveTitleTop" :scrollY="scrollY"></imgcontainer>
    <imgcontainer :bgimg="'4.jpg'" :title="'标题四'" :index="'3'" :leaveTitleIndex="leaveTitleIndex" :leaveTitleTop="leaveTitleTop" :scrollY="scrollY"></imgcontainer>
  </div>
</template>

<script>
import imgcontainer from './components/section'

export default {
  data () {
    return {
      imgArr: [1, 2, 3, 4],
      chooseOne: '',
//     第几个元素的title的index
      leaveTitleIndex: '',
//      第几个元素title的顶部到浏览器顶部的距离
      leaveTitleTop: '',
      scrollY: ''
    }
  },
  name: 'app',
  components: {
    imgcontainer
  },
  mounted () {
    var self = this
    var containerArr = document.getElementsByClassName('container')
    window.addEventListener('scroll', function () {
      self.scrollY = window.scrollY
      for (var i = 0; i < containerArr.length; i++) {
        var itemtitle = document.querySelector('.title' + i)
        var titleTop = itemtitle.offsetTop - window.scrollY
        if (titleTop > -window.innerHeight / 2 && titleTop < window.innerHeight / 2) {
          self.leaveTitleTop = titleTop
          self.leaveTitleIndex = i
        }
      }
    })
  }
}
</script>

<style>

</style>
