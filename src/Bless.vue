<template>
  <div class="begin">
    <div class="begin_backg">
      <img style="margin-top: -20px" src="../img/begin.png" alt="">
    </div>
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
    </div>
    <div class="begin_bg">
      <img  src="../img/before_kt.png" alt="">
    </div>

    <div class="word_b">
      <p>{{bless.from}}给</p>
      <p><span>{{bless.to}}</span></p>
      <p>磕了{{bless.total}}个头</p>
    </div>

    <vue-smart-button class="wantkt">
      <div slot="down"  @click="alsoplay">
        <img src="../img/btn_want.png" alt="">
      </div>
      <div slot="up"  @click="alsoplay">
        <img src="../img/btn_want2.png" alt="">
      </div>
    </vue-smart-button>
    <vue-smart-button  class="begin_ranking">
      <div slot="down"  @click="ranking">
        <img src="../img/btn_ranking.png" alt="">
      </div>
      <div slot="up"  @click="ranking">
        <img src="../img/paihangbang2.png" alt="">
      </div>
    </vue-smart-button>

  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueSmartButton from 'vue-smart-button'
    export default {
        name: "bless",
      props:{
          bless:{default:{}}
      },
      data:function () {
        return {}
      },
      methods:{
        alsoplay:function () {
         this.$emit('state','kowtow')

        }, ranking:function () {
         this.$emit('state','toplist')
        }
      },
      components:{VueSmartButton:VueSmartButton},
      mounted:function () {
        fastclick.attach(this.$el)
      }
    }
</script>

<style scoped>
  .begin{
    width: 100%;height:100%;
    position: relative;

  }
  .begin_backg{
    width: 740px;height:100%;
    position: absolute;left:-50px;top:0;
  }
  .begin_game{
    width: 100%;height:100%;
    background-image: url("../img/begin.png");position: relative;
    background-size: 840px 100%;background-position: -100px 0;
  }
  .rotate{
    width: 740px;height:422px;position: absolute;
    left:-50px;top:0;
  }
  .rotate_left{
    width: 461px;height:460px;position: absolute;
    left: -133px;top:-38px;animation: rotate 10s infinite linear;
  }
  .rotate_right{
    width: 461px;height:460px;position: absolute;
    right:-133px;top:-38px;animation: rotates 10s infinite linear;
  }
  @keyframes rotate {
    0%{
      transform: rotate(0deg);
    }
    25%{
      transform: rotate(90deg);
    }
    50%{
      transform: rotate(180deg);
    }
    75%{
      transform: rotate(270deg);
    }
    100%{
      transform: rotate(360deg);
    }
  }
  @keyframes rotates {
    0%{
      transform: rotate(0deg);
    }
    25%{
      transform: rotate(-90deg);
    }
    50%{
      transform: rotate(-180deg);
    }
    75%{
      transform: rotate(-270deg);
    }
    100%{
      transform: rotate(-360deg);
    }
  }
  .dog_right{
    width: 91px;height:91px;
    position: absolute;
    top:133px;right:38px;
  }
  .dog_left{
    width: 91px;height:91px;
    position: absolute;
    top: 133px;left:39px;
  }
  .begin_bg{
    width: 740px;height:1024px;position: absolute;
    bottom:0;left:-50px;
  }

  .word_b{
    width: 100%;height: 229px;
    position: absolute;left:-8px;top:-6px;bottom:0;margin:auto;
    font-size: 76px;color: #000;font-weight: bolder;text-align: center;
    line-height: 80px;
    text-shadow:4px 5px 0px #fff100;
  }
  .wantkt{
    width: 265px;height:169px;
    position: absolute;bottom:10px;left:10px;
  }
  .btn_want{
    position: absolute;left:0;top:0;
  }
  .btn_want2{
    position: absolute;
    left: 0;top:0;
  }
  .begin_ranking{
    width: 265px;height:169px;
    position: absolute;bottom:10px;right:10px;
  }
</style>
