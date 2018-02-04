<template>
  <div class="begin_game" style="margin-top: -10px">
    <div class="rotate">
      <div class="rotate_right">
        <img src="../img/rotate_left.png" alt="">
      </div>
      <div class="rotate_left">
        <img src="../img/rotate_left.png" alt="">
      </div>
      <div class="dog_right">
        <img src="../img/dog_right.png" alt="">
      </div>
      <div class="dog_left">
        <img src="../img/dog_left.png" alt="">
      </div>
      <div class="blue_left">
        <img src="../img/blue_left.png" alt="">
      </div>
      <div class="blue_right">
        <img src="../img/blue_right.png" alt="">
      </div>
    </div>
    <div class="begin_bg">
      <img  src="../img/bg.png" alt="">
    </div>
    <transition name="downup" mode="out-in" appear>
      <div v-show="true" class="begin_kt" @click="begin_play">
        <img src="../img/begin_kt.png" alt="">
      </div>
    </transition>
    <div class="pay_year" ref="pay_year">
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year ti" ref="lang">
          <img src="../img/ti.png" alt="">
        </div>
      </transition>
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year ni" ref="lang">
          <img src="../img/ni.png" alt="">
        </div>
      </transition>
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year gei" ref="lang">
          <img src="../img/gei.png" alt="">
        </div>
      </transition>
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year da" ref="lang">
          <img src="../img/da.png" alt="">
        </div>
      </transition>
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year jia" ref="lang">
          <img src="../img/jia.png" alt="">
        </div>
      </transition>
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year bai" ref="lang">
          <img src="../img/bai.png" alt="">
        </div>
      </transition>
      <transition name="fade" mode="out-in" appear>
        <div v-show="true" class="year nian" ref="lng">
          <img src="../img/nian.png" alt="">
        </div>
      </transition>

    </div>

  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueSmartButton from 'vue-smart-button'

  export default {
    name: "bless",
    props: {},
    data: function () {
      return {}
    },
    methods: {
      begin_play: function () {
        this.$emit('state', 'kowtow')

      }
    },
    components: {VueSmartButton: VueSmartButton},
    mounted: function () {
      fastclick.attach(this.$el)
    }
  }
</script>

<style scoped>


  .downup-enter-active, .downup-leave-active {
    transition: all .8s;
    transition-delay: 1.4s;
    opacity: 1;
    transform: translate(0px, 0px);
  }

  .downup-enter, .downup-leave-to {
    opacity: 0;

    transform: translate(0px, 50px);
  }

  .fade-enter-active, .fade-leave-active {
    transition: all .5s;
    opacity: 1;
    transform: scale(1, 1);
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;

    transform: scale(2.5, 2.5);
  }

  .begin_game {
    width: 100%;
    height: 100%;
    background-image: url("../img/begin.png");
    position: relative;
    background-size: 840px 100%;
    background-position: -100px 0;
  }

  .rotate {
    width: 740px;
    height: 422px;
    position: absolute;
    left: -50px;
    top: 0;
    overflow: hidden;
  }

  .rotate_left {
    width: 461px;
    height: 460px;
    position: absolute;
    left: -133px;
    top: -38px;
    animation: rotate 10s infinite linear;
  }

  .rotate_right {
    width: 461px;
    height: 460px;
    position: absolute;
    right: -133px;
    top: -38px;
    animation: rotates 10s infinite linear;
  }

  @keyframes rotate {
    0% {
      transform: rotate(0deg);
    }
    25% {
      transform: rotate(90deg);
    }
    50% {
      transform: rotate(180deg);
    }
    75% {
      transform: rotate(270deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  @keyframes rotates {
    0% {
      transform: rotate(0deg);
    }
    25% {
      transform: rotate(-90deg);
    }
    50% {
      transform: rotate(-180deg);
    }
    75% {
      transform: rotate(-270deg);
    }
    100% {
      transform: rotate(-360deg);
    }
  }

  .dog_right {
    width: 91px;
    height: 91px;
    position: absolute;
    top: 133px;
    right: 38px;
  }

  .dog_left {
    width: 91px;
    height: 91px;
    position: absolute;
    top: 133px;
    left: 39px;
  }

  .begin_bg {
    width: 740px;
    height: 1024px;
    position: absolute;
    bottom: 0;
    left: -50px;
  }

  .word_y {
    width: 100%;
    height: 229px;
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    margin: auto;
    font-size: 76px;
    color: #fff100;
    font-weight: bolder;
    text-align: center;
    line-height: 80px;
  }

  .word_b {
    width: 100%;
    height: 229px;
    position: absolute;
    left: -8px;
    top: -6px;
    bottom: 0;
    margin: auto;
    font-size: 76px;
    color: #000;
    font-weight: bolder;
    text-align: center;
    line-height: 80px;
  }

  .wantkt {
    width: 265px;
    height: 169px;
    position: absolute;
    bottom: 10px;
    left: 10px;
  }

  .btn_want {
    position: absolute;
    left: 0;
    top: 0;
  }

  .btn_want2 {
    position: absolute;
    left: 0;
    top: 0;
  }

  .btn_ranking {
    width: 265px;
    height: 169px;
    position: absolute;
    bottom: 10px;
    right: 10px;
  }

  .begin_ranking {
    width: 265px;
    height: 169px;
    position: absolute;
    bottom: 0px;
    right: 0px;
  }

  .begin_ranking2 {
    position: absolute;
    left: 0;
    top: 0;
  }

  .blue_left {
    width: 88px;
    height: 172px;
    position: absolute;
    top: 58px;
    left: 46px;
  }

  .blue_right {
    width: 99px;
    height: 104px;
    position: absolute;
    top: 71px;
    right: 12px;
  }

  .begin_kt {
    width: 264px;
    height: 169px;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 10px;
    margin: auto;
  }

  .pay_year {
    width: 50px;
    height: 540px;
    position: absolute;
    left: 295px;
    top: 276px;
  }

  .year {
    width: 50px;
    height: 50px;
    position: absolute;
    left: 0;
    top: 0;
  }

  .ti {
    transition-delay: 0s;
  }

  .ni {
    transition-delay: 0.2s;
    top: 80px
  }

  .gei {
    transition-delay: 0.4s;
    top: 160px
  }

  .da {
    transition-delay: 0.6s;
    top: 240px
  }

  .jia {
    transition-delay: 0.8s;
    top: 320px
  }

  .bai {
    transition-delay: 1s;
    top: 400px
  }

  .nian {
    transition-delay: 1.2s;

    top: 480px;
  }
</style>
