<template>

    <div class="ranking" >
      <div class="ranking_bg"></div>
      <div class="ranking_rotate">
        <vue-movie-clip ref="my_movieclip" :auto-play="true" :init-frame="1" width="740px"
                        height="1020px" type="canvas" v-show="true" :frame-time="500"
                        :frame="1" :frames="frames"
                        :loop="true" :forward="true"
        >


        </vue-movie-clip>
      </div>
      <div class="top_person">
        <img src="../img/line_up.png" alt="">
      </div>
      <div class="paihangbang">
        <img src="../img/paihangbang.png" alt="">
      </div>
      <div class="pa_left">
        <img src="../img/climb_left.png" alt="">
      </div>
      <div class="pa_right">
        <img src="../img/climb_right.png" alt="">
      </div>
      <div class="rank_kt" @click="alsoplay">
        <img src="../img/btn_want.png" alt="">
      </div>
      <div class="rank_replenish">
        <img src="../img/replenish.png" alt="">
      </div>
      <!--<div class="process">-->
        <!--<img src="../img/frame.png" alt="">-->
        <!--<div class="bar">-->
          <!--<img src="../img/bar.png" alt="">-->
        <!--</div>-->
      <!--</div>-->
      <div class="rank_order">
        <p v-for="(node, index) in list" :class="{'yel':index<=2}">NO{{index+1}}. {{node.nickname}}</p >
        <!--<p class="yel">NO2.谁都不是人啊</p >-->
        <!--<p class="yel">NO3.谁都不是人啊</p >-->
        <!--<p>NO4.谁都不是人啊</p >-->
        <!--<p>NO5.谁都不是人啊</p >-->
        <!--<p>NO6.谁都不是人啊</p >-->
        <!--<p>NO7.谁都不是人啊</p >-->
      </div>

    </div>


</template>

<script>
  import fastclick from 'fastclick'
  import VueSmartButton from 'vue-smart-button'
  import VueMovieClip from 'vue-movie-clip'
  import JohnnyUtils from 'johnny-utils'
  import jsonp from 'jsonp'



let frames=[]
  frames.push('../img/ranking/00001.png', '../img/ranking/00002.png', '../img/ranking/00003.png')
  export default {
    name: "game",
    props: {server:{default:'/'}},
    data: function () {
      return {frames:frames,list:[]}
    },
    computed: {

    },
    methods: {
      alsoplay: function () {
        this.$emit('state', 'home')

      }
    },
    components: {VueSmartButton: VueSmartButton, VueMovieClip: VueMovieClip},
    mounted: function () {
      fastclick.attach(this.$el)

let self=this;
      jsonp(this.server+'/home/toplist/', {
        param: JohnnyUtils.Data.objectToString({}) + '&callback',
        timeout:60000,
        prefix: '__jsonp_j_'
      }, (err, data) => {
        if (err && error) {
          error(err)
        } else {
          self.list=data.data
          //console.log('success',data);
        }
      })



    }
  }
</script>

<style scoped>
  .ranking{
    width: 100%;height:100%;
  }
  .ranking_bg{
    width: 740px;height:100%;background: #ff5400;position: relative;margin-left: -50px;
  }
  .ranking_rotate{
    width: 740px;height:100%;position: absolute;left:-50px;top:0;
  }
  .rank_kt{
    width: 265px;height:169px;
    position: absolute;left:10px;bottom:10px;
  }
  .rank_replenish{
    width: 265px;height:169px;
    position: absolute;right:10px;bottom:10px;
  }
  .top_person{
    width: 620px;height:97px;
    position: absolute;left:10px;top:9px;
  }
  .paihangbang{
    width: 94px;height:290px;position: absolute;
    left:272px;top:51px;
  }
  .pa_left{
    width: 192px;height:120px;
    position: absolute;left:62px;top:183px;
  }
  .pa_right{
    width: 192px;height:120px;
    position: absolute;right:62px;top:183px;
  }
  .process{
    width: 57px;height:441px;
    position: absolute;right:10px;top:369px;
  }
  .bar{
    width: 57px;height:233px;
    position: absolute;top:100px;left:0;
  }
  .rank_order{
    width: 100%;height:437px;position: absolute;left:0;top:374px;
  }
  .rank_order>p{
    font-size: 36px;line-height: 56px;
    color: #000;text-align: center;font-weight: bolder;
  }
  .rank_order>.yel{
    color: #fff100;
  }
</style>
