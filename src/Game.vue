<template>
  <div class="game">
    <div class="game_bg">
      <img src="../img/game_bg.png" alt="">
    </div>
    <div class="grade">
      <img src="../img/grade_btn.png" alt="">
      <p>{{displayNum}}</p>
    </div>
    <div class="hint" v-if="num<=0">
      <img src="../img/hint.png" alt="">
    </div>
    <div class="kt3" @touchstart="kowtow">
      <vue-movie-clip ref="kowtow_mc" :auto-play="false" :init-frame="1" width="340px"
                      height="517px" type="canvas" v-show="true" :frame-time="50"
                      :frame="1" :frames="kt"
                      :loop="false" :forward="true" @stop="onKowtowStop" @play="onKowtowPlay">

      </vue-movie-clip>
    </div>
    <!--<div class="easter_heart" v-show="num==5">-->
    <!--<div class="heart" ref="heart">-->
    <!--< img src="../img/heart.png" alt="">-->
    <!--</div>-->
    <!--</div>-->
    <!--<div class="dog" v-show="num==8">-->
    <!--<vue-movie-clip ref="dog" :auto-play="false" :init-frame="1" width="193px"-->
    <!--height="454px" type="canvas" v-show="true" :frame-time="100"-->
    <!--:frame="1" :frames="dog"-->
    <!--:loop="false" :forward="true" >-->

    <!--</vue-movie-clip>-->
    <!--</div>-->


    <div class="game_btn" v-if="showEndPanel"  >
      <vue-smart-button class="again" >
        <div slot="down" >
          <img src="../img/again2.png" @click="showEndPanel=false" alt="">
        </div>
        <div slot="up"  >
          <img src="../img/again.png" @click="showEndPanel=false" alt="">
        </div>
      </vue-smart-button>


      <vue-smart-button  class="rest"  >
        <div slot="down" >
          <img src="../img/rest2.png" @click="endGame" alt="">
        </div>
        <div slot="up"  >
          <img src="../img/rest.png" @click="endGame"  alt="">
        </div>
      </vue-smart-button>


    </div>

  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueSmartButton from 'vue-smart-button'
  import VueMovieClip from 'vue-movie-clip'


  let kt = []
  kt.push('../img/active1.png', '../img/active2.png', '../img/active2.png', '../img/active2.png', '../img/active3.png', '../img/active3.png', '../img/active4.png', '../img/active1.png')

  let timeout_iv

  function PrefixInteger(num, n) {
    return (Array(n).join(0) + num).slice(-n);
  }

  export default {
    name: "game",
    props: {},
    data: function () {
      return {num: 0, kt: kt, enabled: true, showEndPanel: false}
    },
    computed: {
      displayNum: function () {
        return PrefixInteger(this.num, 3)
      }
    },
    methods: {
      kowtow: function () {
        if (this.enabled) {
          clearTimeout(timeout_iv);
          this.num++;
          this.$refs.kowtow_mc.play()
          this.$emit('total',  this.num)
          this.$emit('playMp3', './media/kowtow.mp3')
          timeout_iv = setTimeout(this.endPanel, 1000)
        }
      },
      endPanel: function () {
        this.showEndPanel = true;


      },
      endGame:function () {
        this.$emit('state', 'gameover')
      },


      onKowtowStop: function () {
        this.enabled = true
      },
      onKowtowPlay: function () {
        this.enabled = false
      },
      alsoplay: function () {
        this.$emit('state', 'kowtow')

      }, ranking: function () {
        this.$emit('state', 'toplist')
      }
    },
    components: {VueSmartButton: VueSmartButton, VueMovieClip: VueMovieClip},
    mounted: function () {
      fastclick.attach(this.$el)
    }
  }
</script>

<style scoped>
  .game {
    width: 100%;
    height: 100%;
    position: relative;
  }

  .game_bg {
    width: 740px;
    height: 100%;
    position: absolute;
    left: -50px;
    top: 0;
  }

  .grade {
    position: absolute;
    width: 208px;
    height: 86px;
    right: 22px;
    top: 55px;
  }

  .grade > p {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    font-size: 46px;
    color: #fff;
    font-weight: bolder;
    text-align: center;
    line-height: 86px;
  }

  .hint {
    width: 132px;
    height: 120px;
    position: absolute;
    left: 51px;
    top: 350px;
    animation: updown 1s infinite linear;
  }

  @keyframes updown {
    0% {
      top: 350px;
    }
    25% {
      top: 340px;
    }
    50% {
      top: 330px;
    }
    75% {
      top: 340px;
    }
    100% {
      top: 350px;
    }
  }

  .kt3 {
    width: 340px;
    height: 517px;
    position: absolute;
    left: 132px;
    top: 232px;
  }

  .game_btn {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
  }

  .again {
    width: 169px;
    height: 265px;
    position: absolute;
    left: 10px;
    bottom: 10px;
  }

  .rest {
    width: 169px;
    height: 265px;
    position: absolute;
    right: 10px;
    bottom: 10px;
  }

  .end {
    width: 100%;
    height: 100%;
    position: relative;
    overflow: hidden;
  }

  .end_bg {
    width: 740px;
    height: 100%;
    position: absolute;
    left: -50px;
    top: 0;
  }

  .end_rotate {
    width: 1200px;
    height: 3328px;
    position: absolute;
    left: -276px;
    top: -1250px;
    animation: rotate 10s infinite linear;
    transform-origin: 50% 53%;
  }

  .end_person {
    width: 533px;
    height: 384px;
    position: absolute;
    left: 57px;
    top: 369px;
  }

  .logo {
    width: 138px;
    height: 131px;
    position: absolute;
    right: 132px;
    top: 9px;
  }

  .frame {
    width: 571px;
    height: 414px;
    position: absolute;
    left: 43px;
    top: 10px;
  }

  .endword_y {
    width: 100%;
    height: 206px;
    position: absolute;
    left: 0;
    top: 121px;
    font-size: 66px;
    color: #ffff39;
    font-weight: bolder;
    text-align: center;
    line-height: 70px;
  }

  .endword_b {
    width: 100%;
    height: 206px;
    position: absolute;
    left: -7px;
    top: 116px;
    font-size: 66px;
    color: #000;
    font-weight: bolder;
    text-align: center;
    line-height: 70px;
  }

  .endword_b > p > span {
    color: #c9caca;
  }

  .tags {
    width: 436px;
    height: 265px;
    position: absolute;
    left: 10px;
    bottom: 11px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .baba {
    width: 109px;
    height: 89px;
  }

  .nanpengyou {
    width: 145px;
    height: 89px;
  }

  .jinli {
    width: 181px;
    height: 89px;
  }

  .bainian {
    width: 169px;
    height: 265px;
    position: absolute;
    right: 9px;
    bottom: 10px;
  }

  .ranking {
    width: 100%;
    height: 100%;
  }

  .ranking_bg {
    width: 740px;
    height: 100%;
    background: #ff5400;
    position: relative;
    margin-left: -50px;
  }

  .ranking_rotate {
    width: 740px;
    height: 100%;
    position: absolute;
    left: -50px;
    top: 0;
  }

  .rank_kt {
    width: 265px;
    height: 169px;
    position: absolute;
    left: 10px;
    bottom: 10px;
  }

  .rank_replenish {
    width: 265px;
    height: 169px;
    position: absolute;
    right: 10px;
    bottom: 10px;
  }

  .top_person {
    width: 620px;
    height: 97px;
    position: absolute;
    left: 10px;
    top: 9px;
  }

  .paihangbang {
    width: 94px;
    height: 290px;
    position: absolute;
    left: 272px;
    top: 51px;
  }

  .pa_left {
    width: 192px;
    height: 120px;
    position: absolute;
    left: 62px;
    top: 183px;
  }

  .pa_right {
    width: 192px;
    height: 120px;
    position: absolute;
    right: 62px;
    top: 183px;
  }

  .process {
    width: 57px;
    height: 441px;
    position: absolute;
    right: 10px;
    top: 369px;
  }

  .bar {
    width: 57px;
    height: 233px;
    position: absolute;
    top: 100px;
    left: 0;
  }

  .rank_order {
    width: 100%;
    height: 437px;
    position: absolute;
    left: 0;
    top: 374px;
  }

  .rank_order > p {
    font-size: 36px;
    line-height: 56px;
    color: #000;
    text-align: center;
    font-weight: bolder;
  }

  .rank_order > .yel {
    color: #fff100;
  }

  .fuceng {
    width: 100%;
    height: 100%;
    background: url("../img/fuceng_bg.png") no-repeat center;
    position: relative;
    background-size: 740px 100%;
    background-position: -50px 0;
  }

  .hand {
    width: 130px;
    height: 189px;
    position: absolute;
    left: 232px;
    top: 448px;
  }

  .light {
    width: 369px;
    height: 563px;
    position: absolute;
    right: 9px;
    top: 10px;
  }

  .ni-enter-to {
    top: 80px;
  }

  .ni-enter-active {
    transition: all 2s;
  }

  .easter_heart {
    width: 300px;
    height: 200px;
    position: absolute;
    left: 145px;
    top: 260px;
  }

  .heart {
    width: 50px;
    height: 38px;
    position: absolute;
    left: 0;
    bottom: 0;
    animation: heart 3s linear;
    opacity: 0;
  }

  @keyframes heart {
    0% {
      opacity: 0;
      bottom: 0;
    }
    50% {
      opacity: 1;
      bottom: 100px;
    }
    75% {
      opacity: 0;
      bottom: 180px;
    }
    100% {
      opacity: 0;
      bottom: 200px;
    }
  }

  .dog {
    width: 193px;
    height: 454px;
    position: absolute;
    right: 0;
    bottom: 110px;
  }
</style>
