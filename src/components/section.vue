<template>
  <div class="container" :class="'container' + index ">
    <div class="bgimg" :style="imgStyle">
      <div class="title" :class="'title' + index" :style="titleLeave">
        <h1>{{title}}</h1>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: ['bgimg', 'title', 'index', 'leaveTitleIndex', 'leaveTitleTop', 'scrollY'],
    data () {
      return {
        container: []
      }
    },
    computed: {
      titleLeave () {
        if (this.index + '' === this.leaveTitleIndex + '') {
          return { opacity: this.leaveTitleTop / (window.innerHeight / 2), transform: 'translateY(' + (-10000) / this.leaveTitleTop + 'px)' }
        } else {
          return { opacity: '1' }
        }
      },
      imgStyle () {
        return { backgroundPosition: '50% ' + this.scrollY * 100 / document.body.offsetHeight + '%', backgroundImage: 'url( /static/img/' + this.bgimg + ')', backgroundSize: 'auto 140vh' }
      }
    }
  }
</script>

<style scoped>
.container{
  height: 100vh;
}
.bgimg{
  height: 100vh;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding: 0px 40px 0px 40px;
}
  .title{
    font-size: 30px;
    color: ghostwhite;
    background-color: rgba(0, 0, 0, 0.5);
    width: 40%;
    text-align: right;
    padding:0px 40px;
  }
</style>
