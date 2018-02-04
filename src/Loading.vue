<template>
  <div class="loading">
    <div class="loading_scroll">
      <img class="img-100" style="display: block" src="../img/loading1.png"/>
      <img class="img-100" style="display: block" src="../img/loading2.png"/>
      <img class="img-100" style="display: block" src="../img/loading1.png"/>
    </div>
    <vue-movie-clip class="loading_movie" :auto-play="true" :init-frame="1" width="640px"
                    height="1040px" type="canvas" v-show="true" :frame-time="100"
                    :frame="1" :frames="loading"
                    :loop="true" :forward="true">

    </vue-movie-clip>
  </div>
</template>

<script>
  import VueMovieClip from 'vue-movie-clip'
  import SmartLoader from 'smart-loader'

  let loading = []
  loading.push('./img/loading1_ps.png', './img/loading2_ps.png')

  export default {
    components: {VueMovieClip: VueMovieClip}, data: function () {
      return {loading: loading}
    },
    methods: {},
    name: "loading",
    mounted: function () {
      let self = this;

      let mintime=1000
      let start=new Date().getTime()

      let loader = new SmartLoader({capacity: 2})
      loader.addImage('./img/loading1.png')
      loader.addImage('./img/loading2.png')
      loader.addImage('./img/loading1_ps.png')
      loader.addImage('./img/loading2_ps.png')
      loader.addImage('./img/begin.png')
      loader.addImage('./img/begin_kt.png')
      loader.addImage('./img/bg.png')
      loader.addImage('./img/ranking/00001.png')
      loader.addImage('./img/ranking/00002.png')
      loader.addImage('./img/ranking/00003.png')

      /*for (let i = 1; i < 3; i++) {
        loader.addImage('../img/loading/' + PrefixInteger(i, 5) + '.png',['image'],9)
      }*/
      loader.addCompletionListener(function () {
        let now=new Date().getTime();
        if(now-start<mintime){
          setTimeout(function () {
            self.$emit('complete')
          },mintime-(now-start))

        }else{
          self.$emit('complete')
        }


      });

      loader.start();
    }

  }
</script>

<style scoped>
  .loading {
    width: 100%;
    height: 100%;
    background-color: aqua;
  }

  .loading_scroll {
    width: 740px;
    margin-left: -50px;
    position: relative;
    animation: loading_scroll 2s infinite linear;
  }

  @keyframes loading_scroll {
    0% {
      top: 0px;
    }
    100% {
      top: -2404px;
    }

  }

  .loading_movie {
    position: absolute;
    top: 0px;
    left: 0px;
  }


</style>
