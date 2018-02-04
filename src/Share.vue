<template>

  <div class="fuceng" @click="share">
    <img width="680" style="margin-left: -20px;margin-top: -30px" src="../img/fuceng_bg.png"/>
    <div class="light">
      <img src="../img/fuceng_light.png" alt="">
    </div>
    <div class="hand">
      <img src="../img/hand.png" alt="">
    </div>
  </div>

</template>

<script>

  export default {
    components: {}, data: function () {
      return {}
    },
    methods: {share:function () {
        this.$emit('share', false);
      }},
    name: "loading",
    mounted: function () {

    }

  }
</script>

<style scoped>

  .fuceng{
    position: absolute;

    left: 0px;top: 0px;
  }
  .hand{
    width: 130px;height:189px;position: absolute;left:253px;top:448px;
  }
  .light{
    width: 369px;height:563px;
    position: absolute;right:9px;top:10px;
  }

</style>
