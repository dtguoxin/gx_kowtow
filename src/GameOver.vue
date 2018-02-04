<template>
  <div class="end">
    <div class="end_bg">
      <img src="../img/end_bg.png" alt="">
    </div>
    <div class="end_rotate">
      <img style="width: 100%;height: 100%" src="../img/end_rotate.png" alt="">
    </div>
    <div class="logo">
      <img src="../img/wufangzhai.png" alt="">
    </div>
    <div class="end_person">
      <img src="../img/end_person.png" alt="">
    </div>
    <div class="frame">
      <img src="../img/word_bg.png" alt="">
      <div class="word_b">
        <p>{{bless.from}}给</p>
        <p>
          <!--<span>{{bless.to}}</span>-->
          <input class="to_name" v-model="bless.to"/>
        </p>
        <p>磕了{{bless.total}}个头</p>
      </div>

    </div>
    <div class="tags">
      <div class="baba" @click="changeTo('爸爸')">
        <img src="../img/baba.png" alt="">
      </div>
      <div class="baba" @click="changeTo('妈妈')">
        <img src="../img/mama.png" alt="">
      </div>
      <div class="baba" @click="changeTo('爷爷')">
        <img src="../img/yeye.png" alt="">
      </div>
      <div class="baba" @click="changeTo('奶奶')">
        <img src="../img/nainai.png" alt="">
      </div>
      <div class="nanpengyou" @click="changeTo('男朋友')">
        <img src="../img/nanpengyou.png" alt="">
      </div>
      <div class="nanpengyou" @click="changeTo('女朋友')">
        <img src="../img/nvpengyou.png" alt="">
      </div>
      <div class="nanpengyou" @click="changeTo('财神爷')">
        <img src="../img/caishenye.png" alt="">
      </div>
      <div class="jinli" @click="changeTo('运势锦鲤')">
        <img src="../img/jinli.png" alt="">
      </div>
      <div class="baba" @click="changeTo('水逆')">
        <img src="../img/shuini.png" alt="">
      </div>
      <div class="nanpengyou" @click="changeTo('外星人')">
        <img src="../img/waixingren.png" alt="">
      </div>
    </div>
    <div class="bainian" @click="share">
      <img src="../img/bainian.png" alt="">
    </div>
  </div>
</template>

<script>
  import fastclick from 'fastclick'
  import VueSmartButton from 'vue-smart-button'
  import JohnnyUtils from 'johnny-utils'
  import jsonp from 'jsonp'

  export default {
    name: "bless",
    props: {
      bless: {default: {}}
      ,server:{default:'/'}
    },
    data: function () {
      return {share_div: false}
    },
    methods: {
      changeTo: function (nickname) {
        this.bless.to = nickname;

      },
      share: function () {
        let self=this;
        jsonp(this.server+'/home/kowtow/', {
          param: JohnnyUtils.Data.objectToString(this.bless) + '&callback',
          timeout:60000,
          prefix: '__jsonp_share_'
        }, (err, data) => {
          if (err && error) {
            error(err)
          } else {

            window.WECHAT_SHARE.set('appmessage', 'title', self.bless.from+"给"+self.bless.to+'磕了'+self.bless.total+'个响头');
            window.WECHAT_SHARE.set('appmessage', 'link', data.data.url);
            window.WECHAT_SHARE.set('timeline', 'title', self.bless.from+"给"+self.bless.to+'磕了'+self.bless.total+'个响头');
            window.WECHAT_SHARE.set('timeline', 'link', data.data.url);
            window.WECHAT_SHARE.update();
            console.log('success',data.data.url);
          }
        })

        this.$emit('share', true);
      },

      alsoplay: function () {
        this.$emit('state', 'kowtow')

      }, ranking: function () {
        this.$emit('state', 'toplist')
      }

    },
    components: {VueSmartButton: VueSmartButton},
    mounted: function () {
      fastclick.attach(this.$el)
    }
  }
</script>

<style scoped>
  .to_name {
    font-size: 66px;
    color: #000;
    font-weight: bolder;
    text-align: center;
    width: 100%;
    background: rgba(0, 0, 0, 0);
    border: 0px;
    text-shadow: 4px 5px 0px #fff100;
  }

  .word_b {
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

    text-shadow: 4px 5px 0px #fff100;
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
</style>
