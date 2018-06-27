# 百度地图web--拖拽选址

> 实现地图拖拽选址功能，百度地图并未像[高德地图拖拽选址功能](http://lbs.amap.com/api/javascript-api/example/amap-ui-positionpicker/position-picker) 。由于项目需要，在百度地图的基础上实现简单的拖拽功能。大神掠过～～

### [MapDemo下载](https://github.com/jun454647/MapDemo.git)

实现思路
```
1. 获取地图的中点经纬度。
2. 获取地图拖拽回调事件。
3. 将大头针图片底部固定在地图的正中央。
```
#### 引用百度地图sdk
在index.html中引用
```
<script type="text/javascript" src="//api.map.baidu.com/api?ak=GbhBTuY8EQf5N8iy8Nklz651Gg6l6W1N&type=lite&v=1.0"></script>
```
#### 组件中实现地图
> map 是地图；
center-point 是打头针；
point 是标示地图中点位置；

代码如下：
```
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
    background: url("../../assets/logo-2.png") center no-repeat;
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

```
**大神略过~~,  如有问题，欢迎讨论**



# map

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
