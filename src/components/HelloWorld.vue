<template>
  <div class="map-wrap">
    <div id="map"></div>
    <div class="center-point"></div>
    <div class="point"></div>
  </div>
</template>

<script>
  export default {
    data(){
      return{}
    },
    mounted(){
      this.mapCenter();
    },
    methods: {
      mapCenter(){
        // 百度地图API功能
        var map = new BMap.Map("map");
        var point = new BMap.Point(114.025973657,22.5460535462);
        map.centerAndZoom(point, 14);
        map.addEventListener("dragend",attribute);
        function attribute() {
          console.log(map.centerPoint);
          // alert("地图中点的位置是" + map.centerPoint.lng + "," + map.centerPoint.lat);
        }
      },
    }
  }
</script>

<style scoped>
  .map-wrap{
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
  }
  #map{
    width: 100%;
    height: 100%;
    position: relative;
  }

  .center-point{
    position: absolute;
    left: 0;
    right: 0;
    top: 50%;
    bottom: 0;
    margin: 0 auto;
    margin-top: -50px;
    width: 40px;
    height: 50px;
    background: url("../assets/logo-2.png") center no-repeat;
    background-size: contain;
  }

  .point{
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
    width: 10px;
    height: 10px;
    background: red;
    border-radius: 50%;
  }
</style>
