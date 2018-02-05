<template>
  <div class="game">
    <div class="game_bg">
      <img src="../img/game_bg.png" alt="">
    </div>
    <transition name="fade" mode="out-in" appear>
      <div v-if="num===45" class="game_bg">
        <img src="../img/click1.png"/>
      </div>
    </transition>
    <transition name="fade" mode="out-in" appear>
      <div v-if="num===46" class="game_bg">
        <img src="../img/click2.png"/>
      </div>
    </transition>
    <transition name="fade" mode="out-in" appear>
      <div v-if="num===47" class="game_bg">
        <img src="../img/click3.png"/>
      </div>
    </transition>


    <div v-if="num>=48&&num<=50" style="position: absolute;right: 0px;top:0px">
      <vue-movie-clip :auto-play="true" :init-frame="1" width="640px"
                      height="1240px" type="canvas" v-show="true" :frame-time="110"
                      :frame="1"
                      :frames="['../img/music1.png','../img/music2.png','../img/music3.png']"
                      :loop="true" :forward="true">
      </vue-movie-clip>
    </div>


    <div v-if="num===100" style="position: absolute;right: 0px;top:500px">
      <vue-movie-clip :auto-play="true" :init-frame="1" width="640px"
                      height="350px" type="canvas" v-show="true" :frame-time="110"
                      :frame="1"
                      :frames="['../img/dazhao1_02.png','../img/dazhao2_02.png','../img/dazhao3_02.png','../img/dazhao4_02.png','../img/dazhao5_02.png','../img/dazhao6_02.png','../img/dazhao7_02.png','../img/dazhao8_02.png','']"
                      :loop="false" :forward="true" >
      </vue-movie-clip>
    </div>



    <div class="grade">
      <img src="../img/grade_btn.png" alt="">
      <p>{{displayNum}}</p>
    </div>
    <transition name="fade" mode="out-in" appear>
      <div class="hint" v-if="num<=0">
        <img src="../img/hint.png" alt="">
      </div>
    </transition>
    <div class="kt3" v-show="!bigKowTow">
      <vue-movie-clip ref="kowtow_mc" :auto-play="false" :init-frame="1" width="340px"
                      height="517px" type="canvas" v-show="true" :frame-time="70"
                      :frame="1" :frames="kt"
                      :loop="false" :forward="true" @stop="onKowtowStop" @play="onKowtowPlay">

      </vue-movie-clip>
    </div>

    <div v-if="num===5" style="position: absolute;left: 0px;top:0px">
      <vue-smart-animator style="position: absolute;left: 80px;top:320px" v-for="frames in hearts" :frames="frames"
                          :options="{
                        startFrom: 1,
                        pauseAt: [],
                        prefix: false,
                        count: 4,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }">
        <img src="../img/heart.png" alt="">
      </vue-smart-animator>
    </div>

    <div v-if="num===15" style="position: absolute;left: -75px;top:-80px">
      <vue-smart-animator style="position: absolute;left: 80px;top:-100px" :frames="[{
      styles: {'opacity':1,'top': '800px'},
      configs: {'duration':'600ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    }]" :options="{
                        startFrom: 0,
                        pauseAt: [],
                        prefix: false,
                        count: 1,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }" @next="$refs.tetris2.play()">
        <img src="../img/tetris_1.png" alt="">
      </vue-smart-animator>
      <vue-smart-animator ref="tetris2" style="position: absolute;left: 100px;top:-200px;" :frames="[{
      styles: {'opacity':1,'top': '720px'},
      configs: {'duration':'600ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    }]" :options="options" @next="$refs.tetris3.play()">
        <img src="../img/tetris_2.png" alt="">
      </vue-smart-animator>
      <vue-smart-animator ref="tetris3" style="position: absolute;left: 120px;top:-300px" :frames="[{
      styles: {'opacity':1,'top': '540px'},
      configs: {'duration':'600ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    }]" :options="options" @next="$refs.tetris4.play()">
        <img src="../img/tetris_3.png" alt="">
      </vue-smart-animator>
      <vue-smart-animator ref="tetris4" style="position: absolute;left: 80px;top:-400px" :frames="[{
      styles: {'opacity':1,'top': '420px'},
      configs: {'duration':'600ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    }]" :options="options" @next="$refs.tetris5.play()">
        <img src="../img/tetris_4.png" alt="">
      </vue-smart-animator>
      <vue-smart-animator ref="tetris5" style="position: absolute;left: 80px;top:-500px" :frames="[{
      styles: {'opacity':1,'top': '386px'},
      configs: {'duration':'600ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    }]" :options="options" @next="$refs.tetris6.play()">
        <img src="../img/tetris_5.png" alt="">
      </vue-smart-animator>
      <vue-smart-animator ref="tetris6" style="position: absolute;left: 129px;top:-600px" :frames="[{
      styles: {'opacity':1,'top': '200px'},
      configs: {'duration':'600ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    }]" :options="options">
        <img src="../img/tetris_6.png" alt="">
      </vue-smart-animator>
    </div>


    <div v-if="num===30" style="position: absolute;left: -75px;top:-80px">
      <vue-smart-animator ref="tetris8" style="position: absolute;left: 121px;top:422px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.65,0.65)'},
      configs: {'duration':'250ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="tetris7" style="position: absolute;left: 174px;top:430px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.70,0.70)'},
      configs: {'duration':'250ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" @next="$refs.tetris8.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="tetris6" style="position: absolute;left: 230px;top:439px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.75,0.75)'},
      configs: {'duration':'250ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" @next="$refs.tetris7.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="tetris5" style="position: absolute;left: 289px;top:448px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.80,0.80)'},
      configs: {'duration':'300ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" @next="$refs.tetris6.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="tetris4" style="position: absolute;left: 350px;top:458px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.85,0.85)'},
      configs: {'duration':'300ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" @next="$refs.tetris5.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="tetris3" style="position: absolute;left: 416px;top:468px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.90,0.90)'},
      configs: {'duration':'350ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" @next="$refs.tetris4.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="tetris2" style="position: absolute;left: 490px;top:478px;opacity:0" :frames="[{
      styles: {'opacity':1,transform: 'translate(0px,0px) rotateZ(0deg) scale(0.95,0.95)'},
      configs: {'duration':'400ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" @next="$refs.tetris3.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator style="position: absolute;left: 280px;top:-100px" :frames="[{
      styles: {'opacity':1,'top': '490px'},
      configs: {'duration':'300ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in'}
    },{
      styles: {'opacity':1,'top': '490px'},
      configs: {'duration':'300ms', 'fill-mode': 'forwards', 'timing-function': 'ease-out'}
    },{
      styles: {'opacity':1,'top': '490px','left':'570px'},
      configs: {'duration':'100ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="{
                        startFrom: 0,
                        pauseAt: [],
                        prefix: false,
                        count: 1,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }" @next="$refs.tetris2.play()">
        <img src="../img/majiang_single.png" alt="">
      </vue-smart-animator>


    </div>


    <div v-if="num===40" style="position: absolute;right: 0px;top:480px">
      <vue-movie-clip :auto-play="true" :init-frame="1" width="193px"
                      height="454px" type="canvas" v-show="true" :frame-time="110"
                      :frame="1"
                      :frames="['../img/dog/dog1_03.png', '../img/dog/dog2_03.png', '../img/dog/dog3_03.png', '../img/dog/dog4_03.png', '../img/dog/dog5_03.png', '../img/dog/dog6_03.png', '../img/dog/dog7_03.png', '../img/dog/dog5_03.png', '../img/dog/dog7_03.png']"
                      :loop="false" :forward="true" @stop="onKowtowStop" @play="onKowtowPlay">
      </vue-movie-clip>
    </div>



    <div v-if="num===60" style="position: absolute;left: -75px;top:-80px">
      <vue-smart-animator ref="boat_left" style="position: absolute;left: 0px;top:838px;opacity:0" :frames="[{
      styles: {'opacity':1,left:'75px'},
      configs: {'duration':'400ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options">
        <img src="../img/boat_left.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator ref="boat_right" style="position: absolute;left: 447px;top:1000px;opacity:0" :frames="[{
      styles: {'opacity':1,top:'948px'},
      configs: {'duration':'500ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="options" >
        <img src="../img/boat_right.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator style="position: absolute;left: 400px;top:440px" :frames="[{
      styles: {'opacity':1,'top': '490px','left':'79px'},
      configs: {'duration':'200ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="{
                        startFrom: 0,
                        pauseAt: [],
                        prefix: false,
                        count: 1,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }" @next="$refs.boat_left.play();$refs.boat_right.play()">
        <img src="../img/boat.png" alt="">
      </vue-smart-animator>

    </div>



    <div v-if="num===70" style="position: absolute;left: -75px;top:-80px">
      <vue-smart-animator style="position: absolute;left: 400px;top:440px" :frames="[{
      styles: {'opacity':1,'top': '490px','left':'79px'},
      configs: {'duration':'400ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    },{
      styles: {'opacity':0,'top': '590px','left':'-179px'},
      configs: {'duration':'200ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="{
                        startFrom: 0,
                        pauseAt: [],
                        prefix: false,
                        count: 1,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }" @next="$refs.big_mc.play()">
        <img src="../img/boat.png" alt="">
      </vue-smart-animator>

      <vue-movie-clip ref="big_mc" v-show="bigKowTow" style="left: 185px;top:80px;position: absolute"  :auto-play="false" :init-frame="1" width="471px"
                       height="736px" type="canvas"  :frame-time="110"
                       :frame="1"
                       :frames="['../img/jump3_02.png',  '../img/jump5_02.png',  '../img/jump4_02.png',  '../img/jump2_02.png',  '../img/jump1_02.png',  '../img/jump1_02.png',  '../img/jump1_02.png']"
                       :loop="false" :forward="true" @stop="bigKowTow=false;enabled = true" @play="playBigTow">
      </vue-movie-clip>

    </div>




    <div v-if="num===80" style="position: absolute;left: 0px;top:0px">
      <vue-smart-animator style="position: absolute;left: 80px;top:0px" v-for="(frames,index) in foods" :frames="frames"
                          :options="{
                        startFrom: 1,
                        pauseAt: [],
                        prefix: false,
                        count: 4,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }">
        <img :src="'../img/food'+(index%5+1)+'.png'" alt="">
      </vue-smart-animator>
    </div>





    <transition name="fade" mode="out-in" appear>
    <div v-if="num===120&&gold===false" style="position: absolute;left: -75px;top:-80px">

      <vue-smart-animator style="position: absolute;left: 200px;top:0px" :frames="[{
      styles: {'opacity':1,'top': '490px','left':'200px'},
      configs: {'duration':'400ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    },{
      styles: {'opacity':1,'top': '470px','left':'200px'},
      configs: {'duration':'200ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    },{
      styles: {'opacity':1,'top': '470px','left':'200px'},
      configs: {'duration':'2800ms', 'fill-mode': 'forwards', 'timing-function': 'ease-in-out'}
    }]" :options="{startFrom: 0,
                        pauseAt: [],
                        prefix: false,
                        count: 1,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }" @next="gold=true">
        <img src="../img/gold.png" alt="">
      </vue-smart-animator>

      <vue-smart-animator style="position: absolute;left: 80px;top:0px" v-for="(frames,index) in stars" :frames="frames"
                          :options="{
                        startFrom: 1,
                        pauseAt: [],
                        prefix: false,
                        count: 1,
                        clear: true,
                        applyOnEnd: true,
                        instant: true
                    }">
        <img :src="'../img/gold_light_03.png'" alt="">
      </vue-smart-animator>

    </div>
    </transition>

    <div v-if="num>150" style="position: absolute;right: 0px;top:0px">
      <vue-movie-clip :auto-play="true" :init-frame="1" width="640px"
                      height="1240px" type="canvas" v-show="true" :frame-time="310"
                      :frame="1"
                      :frames="['../img/jinli1.png','../img/jinli2.png','../img/jinli3.png','../img/jinli4.png','../img/jinli3.png','../img/jinli4.png','']"
                      :loop="false" :forward="true">
      </vue-movie-clip>
    </div>

    <!--<div class="dog" v-show="num==8">-->
    <!--<vue-movie-clip ref="dog" :auto-play="false" :init-frame="1" width="193px"-->
    <!--height="454px" type="canvas" v-show="true" :frame-time="100"-->
    <!--:frame="1" :frames="dog"-->
    <!--:loop="false" :forward="true" >-->

    <!--</vue-movie-clip>-->
    <!--</div>-->


    <div style="width: 100%;height: 100%;position:absolute;top: 0;left: 0" @touchstart="kowtow"></div>
    <transition name="fade" mode="out-in" appear>
      <div class="game_btn" v-show="showEndPanel">
        <vue-smart-button class="again">
          <div slot="down" class="again_down" @click="showEndPanel=false">
            <img src="../img/again2.png"  alt="">
          </div>
          <div slot="up" class="again_up" @click="showEndPanel=false">
            <img src="../img/again.png" alt="">
          </div>
        </vue-smart-button>


        <vue-smart-button class="rest">
          <div slot="down">
            <img src="../img/rest2.png" @click="endGame" alt="">
          </div>
          <div slot="up">
            <img src="../img/rest.png" @click="endGame" alt="">
          </div>
        </vue-smart-button>


      </div>
    </transition>

  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueSmartButton from 'vue-smart-button'
  import VueMovieClip from 'vue-movie-clip'
  import VueSmartAnimator from 'vue-smart-animator'
  import _ from 'underscore'

  let kt = []
  kt.push('./img/active1.png', './img/active2.png', './img/active2.png', './img/active2.png', './img/active4.png', './img/active1.png')

  let timeout_iv

  function PrefixInteger(num, n) {
    return (Array(n).join(0) + num).slice(-n);
  }


  let hearts = [];
  let count = 20

  for (let i = 0; i < count; i++) {
    let frames = [];

    frames.push({
      styles: {
        opacity: 0,
        'animation-delay': i * 50 + 'ms',
        transform: 'translate(0px,0px) rotateZ(0deg) scale(0.01,0.01)'
      },
      configs: {'duration': '0ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })
    let x = (Math.random() * 600 - 300);

    let y = (Math.random() * 600 - 300);
    let rotate = 360 / count * i;
    let time = _.random(200, 500)
    let min = 60

    if (x < 0) {
      x -= min
    } else {
      x += min
    }
    if (y < 0) {
      y -= min
    } else {
      y += min
    }

    frames.push({
      styles: {
        opacity: 1,
        'animation-delay': '0ms',
        transform: 'translate(' + x / 2 + 'px,' + y / 2 + 'px) rotateZ(' + rotate + 'deg) scale(0.1,0.1)'
      },
      configs: {'duration': time + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })

    frames.push({
      styles: {opacity: 0, transform: 'translate(' + x + 'px,' + y + 'px) rotateZ(' + rotate + 'deg) scale(0.05,0.05)'},
      configs: {'duration': time + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })
    hearts.push(frames)
  }




  let foods=[];
  for (let i = 0; i < count; i++) {
    let frames = [];
    let x = (Math.random() * 900 - 400);
    let rotate = 360 / count * i;
    let time = _.random(400, 800)
    let y = (2000-time);
    let min = 60

    if (x < 0) {
      x -= min
    } else {
      x += min
    }
    if (y < 0) {
      y -= min
    } else {
      y += min
    }


    frames.push({
      styles: {
        opacity: 1,
        'animation-delay': i * 50 + 'ms',
        transform: 'translate('+x+'px,-'+time+'px) rotateZ(0deg) scale(1,1)'
      },
      configs: {'duration': '0ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })

    frames.push({
      styles: {
        opacity: 1,
        'animation-delay': '0ms',
        transform: 'translate(' + x  + 'px,' + y / 2 + 'px) rotateZ(' + rotate + 'deg) scale(1.4,1.4)'
      },
      configs: {'duration': time + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })

    frames.push({
      styles: {opacity: 1, transform: 'translate(' + x + 'px,' + y + 'px) rotateZ(' + rotate + 'deg) scale(1.5,1.5)'},
      configs: {'duration': time/1.1 + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })
    foods.push(frames)
  }


  let stars=[];
  for (let i = 0; i < count; i++) {
    let frames = [];
    let x = (Math.random() * 600 - 200);
    let rotate = 360+_.random(0,200) ;
    let time = _.random(2400, 2800)
    let y = (Math.random() * 1200 - 200);
    let min = 60
    if (x < 0) {
      x -= min
    } else {
      x += min
    }
    if (y < 0) {
      y -= min
    } else {
      y += min
    }
    frames.push({
      styles: {
        opacity: 0,
        'animation-delay': '0ms',
        transform: 'translate(' + x  + 'px,' + y  + 'px) rotateZ(0deg) scale(.2,.2)'
      },
      configs: {'duration': time + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })
    frames.push({
      styles: {
        opacity: 0,
        'animation-delay': '0ms',
        transform: 'translate(' + x  + 'px,' + y  + 'px) rotateZ(0deg) scale(1.4,1.4)'
      },
      configs: {'duration': time/2 + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })

    frames.push({
      styles: {opacity: 1, transform: 'translate(' + x + 'px,' + y + 'px) rotateZ(' + rotate + 'deg) scale(10.5,10.5)'},
      configs: {'duration': time/1.1 + 'ms', 'fill-mode': 'forwards', 'timing-function': 'linear'}
    })
    stars.push(frames)
  }



  export default {
    name: "game",
    props: {},
    data: function () {
      return {bigKowTow:false,gold:false,
        num: 0, kt: kt, enabled: true, showEndPanel: false, hearts: hearts,foods:foods,stars:stars, options: {
          startFrom: 0,
          pauseAt: [],
          prefix: false,
          count: 1,
          clear: true,
          applyOnEnd: true,
          instant: false
        }
      }
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
          if(this.num!==70){
          this.$refs.kowtow_mc.play()
            this.$emit('playMp3', './media/kowtow.mp3')
            this.$emit('shake')
          }
          this.enabled = false

          this.$emit('total', this.num)

          if(this.num===50){
            this.$emit('playMp3', './media/di.mp3')
          }else if(this.num===51){
            this.$emit('playMp3', './media/di.mp3',true)
          }



          timeout_iv = setTimeout(this.endPanel, 5000)
        }
      },
      playBigTow:function () {
        this.bigKowTow=true;
        this.$emit('playMp3', './media/kowtow.mp3')
      },
      endPanel: function () {
        this.showEndPanel = true;


      },
      endGame: function () {
        this.$emit('state', 'gameover')
      },


      onKowtowStop: function () {
        this.enabled = true
      },
      onKowtowPlay: function () {
        //this.enabled = false
      },
      alsoplay: function () {
        this.$emit('state', 'kowtow')

      }, ranking: function () {
        this.$emit('state', 'toplist')
      }
    },
    components: {VueSmartButton: VueSmartButton, VueMovieClip: VueMovieClip, VueSmartAnimator: VueSmartAnimator},
    mounted: function () {
      fastclick.attach(this.$el)
    }
  }
</script>

<style scoped>
  .fade-enter-active, .fade-leave-active {
    transition: all .2s linear;
    opacity: 1;
    /*transform: scale(1, 1);*/
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
    /*transform: scale(1.5, 1.5);*/
  }

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
    height: 102%;
    margin-top: -1%;
    position: absolute;
    left: 0;
    top: 0;
    background: rgba(0, 0, 0, 0.2);
  }

  .again {
    width: 169px;
    height: 265px;
    position: absolute;
    left: 10px;
    bottom: 10px;
    animation: fade .2s linear;
  }
@keyframes fade {
  0%{
    opacity: 0;
  }
  100%{
    opacity: 1;
  }
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
  @keyframes tetris_rotate {
    0%{
      transform: rotate(90deg);
    }
    50%{
      transform: rotate(45deg);
    }
    100%{
      transform: rotate(0deg);
    }
  }
</style>
