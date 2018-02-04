<template>
  <div id="app" :class="{'shaking':shaking}" style="position: absolute">

      <vue-fix-dom ref="fixdom" width="640px" height="1024px" align="default">
        <loading @complete="oncomplete" v-if="state==='loading'">

        </loading>
        <bless v-if="state==='bless'" :bless="bless" @state="goState">


        </bless>
        <home v-if="state==='home'" @state="goState">

        </home>
        <game v-if="state==='kowtow'" :bless="bless" @state="goState" @playMp3="playMp3" @total="total" @shake="shake">


        </game>
        <game-over v-if="state==='gameover'" :bless="newBless" @share="showShare" :server="server">

        </game-over>

        <toplist v-if="state==='toplist'" @state="goState" :server="server">

        </toplist>

        <share v-show="share_div" @share="showShare"></share>


      </vue-fix-dom>
  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueFixDom from 'vue-fix-dom'
  import Loading from './Loading'
  import Bless from './Bless'
  import Home from './Home'
  import Game from './Game'
  import GameOver from './GameOver'
  import Toplist from './Toplist'
  import Share from './Share'


  let SERVER = 'http://h5.2smart.cn/2018/kowtow/'

  import WechatShare from 'johnny-wechat-share'

  let option={}
  option.api='http://h5.2smart.cn/wechat/js/'
  option.shareData={
    appmessage: {
      title: "云磕头",//好友分享标题
      desc: "云磕头-",//好友分享描述
      img_url: "",//好友分享图片
      link: SERVER //好友分享链接
    }, timeline: {
      title: "云磕头",//朋友圈分享标题
      img_url: "",//朋友圈分享图片
      link: SERVER//朋友圈分享链接
    }
  }

  let shareURL = document.location.href;
  window.WECHAT_SHARE = new WechatShare(encodeURIComponent(shareURL), option);


  //window.bless={from:'小强',to:'bac',total:1390}
  if(!window.newBless){
    window.newBless = {from: '溜溜', to: '三狗蛋子', total: 0}
  }
  // alert(window.newBless)
  let allSound = {}


  export default {
    name: 'app',
    data() {
      return {state: 'loading', bless: window.bless, newBless: window.newBless, share_div: false, server: SERVER,shaking:false}
    },
    methods: {
      shake:function () {
        let self=this;
       this.shaking=true;
       setTimeout(function () {
         self.shaking=false;
       },0.3)
      },
      oncomplete: function () {
        if (window.bless) {
          this.state = 'bless'
        } else {
          this.state = 'home'
        }
      },
      goState: function (state) {
        this.state = state
      },
      playMp3: function (url, stop) {
        if (!allSound.hasOwnProperty(url)) {
          let audio = new Audio()
          audio.src = url;
          allSound[url] = audio
        }
        if (true === stop) {
          allSound[url].pause()
        } else {
          allSound[url].play()
        }

      },
      total: function (num) {
        this.newBless.total = num;
      },
      showShare: function (show) {

        this.share_div = show
      }
    },

    mounted: function () {
      fastclick.attach(this.$el)
    },
    components: {
      Share: Share,
      VueFixDom: VueFixDom,
      Loading: Loading,
      Bless: Bless,
      Game: Game,
      GameOver: GameOver,
      Toplist: Toplist,
      Home: Home
    },
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
  .shaking {
    animation: shaking 0.2s ;
    -webkit-animation:shaking 0.2s ;
  }

  @keyframes shaking {
    0% {
      top: 0px;
    }
    25% {
      top: 5px;
    }
    50% {

      top: -3px;
    }
    75% {

      top: 2px;
    }
    100% {
      top: 0px;
    }
  }
  @-webkit-keyframes shaking {
    0% {
      top: 0px;
    }
    25% {
      top: 5px;
    }
    50% {

      top: -3px;
    }
    75% {

      top: 2px;
    }
    100% {
      top: 0px;
    }
  }



</style>
