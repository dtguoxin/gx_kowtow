<template>
  <div id="app">
    <vue-fix-dom ref="fixdom" width="640px" height="1024px" align="default">
      <loading @complete="oncomplete" v-if="state==='loading'">

      </loading>
      <bless v-if="state==='bless'" :bless="bless" @state="goState">


      </bless>
      <game v-if="state==='kowtow'" :bless="bless" @state="goState" @playMp3="playMp3" @total="total">


      </game>
      <game-over v-if="state==='gameover'" :bless="newBless" @share="showShare">

      </game-over>

      <toplist v-if="state==='toplist'" @state="goState" :server="server">

      </toplist>

      <share v-show="share_div"  @share="showShare"></share>



    </vue-fix-dom>
  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueFixDom from 'vue-fix-dom'
  import Loading from './Loading'
  import Bless from './Bless'
  import Game from './Game'
  import GameOver from './GameOver'
  import Toplist from './Toplist'
  import Share from './Share'


  let SERVER='http://h5.2smart.cn/2018/kowtow/'

  //window.bless={from:'小强',to:'bac',total:1390}
  window.newBless = {from: '溜溜', to: '三狗蛋子', total: 0}


  export default {
    name: 'app',
    data() {
      return {state: 'kowtow', bless: window.bless, newBless: newBless,share_div:false,server:SERVER}
    },
    methods: {
      oncomplete: function () {
        if (window.bless) {
          this.state = 'bless'
        } else {
          this.state = 'kowtow'
        }
      },
      goState: function (state) {
        this.state = state
      },
      playMp3: function (url) {
        let audio = new Audio()
        audio.src = url;
        audio.play()


      },
      total: function (num) {
        this.newBless.total = num;
      },
      showShare:function (show) {

        this.share_div=show
      }
    },

    mounted: function () {
      fastclick.attach(this.$el)
    },
    components: {Share: Share, VueFixDom: VueFixDom, Loading: Loading, Bless: Bless, Game: Game, GameOver: GameOver,Toplist:Toplist},
  }
</script>

<style lang="scss">
  @import "assets/css/base.css";
  @import "assets/css/mobile_h5.css";

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    overflow: hidden;
    width: 100%;
    height: 100%;
  }

</style>
