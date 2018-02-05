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
    <div class="end_light">
      <img src="../img/end_light.png" alt="">
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
      <vue-smart-button class="baba">
        <div slot="up" @click="changeTo('爸爸')" class="tags_up" style="background: url('./img/baba.png') no-repeat center">
          <!--<img src="../img/baba.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('爸爸')" class="tags_down" style="background: url('./img/baba2.png') no-repeat center">
          <!--<img src="../img/baba2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="baba">
        <div slot="up" @click="changeTo('妈妈')" class="tags_up" style="background: url('./img/mama.png') no-repeat center">
          <!--<img src="../img/mama.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('妈妈')" class="tags_down" style="background: url('./img/mama2.png') no-repeat center">
          <!--<img src="../img/mama2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="baba">
        <div slot="up" @click="changeTo('爷爷')" class="tags_up" style="background: url('./img/yeye.png') no-repeat center">
          <!--<img src="../img/yeye.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('爷爷')" class="tags_down" style="background: url('./img/yeye2.png') no-repeat center">
          <!--<img src="../img/yeye2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="baba">
        <div slot="up" @click="changeTo('奶奶')" class="tags_up" style="background: url('./img/nainai.png') no-repeat center">
          <!--<img src="../img/nainai.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('奶奶')" class="tags_down" style="background: url('./img/nainai2.png') no-repeat center">
          <!--<img src="../img/nainai2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="nanpengyou">
        <div slot="up" @click="changeTo('男朋友')" class="tags_up" style="background: url('./img/nanpengyou.png') no-repeat center">
          <!--<img src="../img/nanpengyou.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('男朋友')" class="tags_down" style="background: url('./img/nanpengyou2.png') no-repeat center">
          <!--<img src="../img/nanpengyou2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="nanpengyou">
        <div slot="up" @click="changeTo('女朋友')" class="tags_up" style="background: url('./img/nvpengyou.png') no-repeat center">
          <!--<img src="../img/nvpengyou.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('女朋友')" class="tags_down" style="background: url('./img/nvpengyou2.png') no-repeat center">
          <!--<img src="../img/nvpengyou2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="nanpengyou">
        <div slot="up" @click="changeTo('财神爷')" class="tags_up" style="background: url('./img/caishenye.png') no-repeat center">
          <!--<img src="../img/caishenye.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('财神爷')" class="tags_down" style="background: url('./img/caishenye2.png') no-repeat center">
          <!--<img src="../img/caishenye2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="jinli">
        <div slot="up" @click="changeTo('运势锦鲤')" class="tags_up" style="background: url('./img/jinli.png') no-repeat center">
          <!--<img src="../img/jinli.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('运势锦鲤')" class="tags_down" style="background: url('./img/jinli2.png') no-repeat center">
          <!--<img src="../img/jinli2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="baba">
        <div slot="up" @click="changeTo('水逆')" class="tags_up" style="background: url('./img/shuini.png') no-repeat center">
          <!--<img src="../img/shuini.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('水逆')" class="tags_down" style="background: url('./img/shuini2.png') no-repeat center">
          <!--<img src="../img/shuini2.png" alt="">-->
        </div>
      </vue-smart-button>

      <vue-smart-button class="nanpengyou">
        <div slot="up" @click="changeTo('外星人')" class="tags_up" style="background: url('./img/waixingren.png') no-repeat center">
          <!--<img src="../img/waixingren.png" alt="">-->
        </div>
        <div slot="down" @click="changeTo('外星人')" class="tags_down" style="background: url('./img/waixingren2.png') no-repeat center">
          <!--<img src="../img/waixingren2.png" alt="">-->
        </div>
      </vue-smart-button>
    </div>

    <vue-smart-button class="bainian">
      <div slot="up" @click="share" class="bainian_up">
        <!--<img src="../img/bainian.png" alt="">-->
      </div>
      <div slot="down" @click="share" class="bainian_down">
        <!--<img src="../img/bainian2.png" alt="">-->
      </div>
    </vue-smart-button>
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
    animation: left 1s linear;
  }
  @keyframes left {
    0%{
      left:-446px;
    }
    100%{
      left:10px;
    }
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
    animation: right 1s linear;
  }
  @keyframes right {
    0%{
      right:-180px;
    }
    100%{
      right:10px;
    }
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
  .baba,.nanpengyou,.jinli{
    position: relative;
  }
  .tags_up{
    width: 100%;height:100%;position: absolute;left:0;top:0;
  }
  .tags_down{
    width: 100%;height:100%;position: absolute;left:0;top:0;
  }
  .bainian_up{
    width: 100%;height:100%;position: absolute;left:0;top:0;
    background: url("../img/bainian.png") no-repeat center;
  }
  .bainian_down{
    width: 100%;height:100%;position: absolute;left:0;top:0;
    background: url("../img/bainian2.png") no-repeat center;
  }
  .end_light{
    width: 300px;height:450px;
    position: absolute;right:178px;top:326px;
    animation: end_rotate 4s infinite linear;
    transform-origin: right top;
  }
  @keyframes end_rotate {
    0%{
      transform: rotate(0deg)
    }
    25%{
      transform: rotate(15deg);
    }
    50%{
      transform: rotate(0deg);
    }
    75%{
      transform: rotate(-15deg);
    }
    100%{
      transform: rotate(0deg);
    }
  }
</style>
