<template>
  <div>
    <div style="position:relative;">
      <swiper :show-dots="false" :list="demo01_list" v-model="demo01_index" @on-index-change="demo01_onIndexChange" auto>
      </swiper>
      <ul class="swiper-item-click">
        <li v-for="(item, index) in demo01_list" :class="{ 'swiper-item-click-active': demo01_index === index }" @click.stop="demo01_onIndexChange(index)"></li>
      </ul>
    </div>
  </div>
</template>

<script>
  import { Swiper, GroupTitle, SwiperItem, XButton, Divider } from 'vux'

  const baseList = [{
    url: 'javascript:',
    img: 'https://static.vux.li/demo/1.jpg',
    title: '送你一朵fua'
  }, {
    url: 'javascript:',
    img: 'https://static.vux.li/demo/2.jpg',
    title: '送你一辆车'
  }, {
    url: 'javascript:',
    img: 'https://static.vux.li/demo/3.jpg',
    title: '送你一次旅行'
  }]

  const imgList = [
    'http://placeholder.qiniudn.com/800x300/FF3B3B/ffffff',
    'http://placeholder.qiniudn.com/800x300/FFEF7D/ffffff',
    'http://placeholder.qiniudn.com/800x300/8AEEB1/ffffff'
  ]

  const only2List = baseList.slice(0, 2)

  export default {
    components: {
      Swiper,
      SwiperItem,
      GroupTitle,
      XButton,
      Divider
    },
    methods: {
      onSwiperItemIndexChange (index) {
        console.log('demo item change', index)
      },
      demo01_onIndexChange (index) {
        this.demo01_index = index
        console.log(this.demo01_index)
      }
    },
    data () {
      return {
        demo01_list: baseList,
        demo01_index: 0,
        swiperItemIndex: 1
      }
    }
  }
</script>

<style lang="scss" scoped>
  $swiper-click-default: white;
  $swiper-click-active: red;

  .copyright {
    font-size: 12px;
    color: #ccc;
    text-align: center;
  }
  .text-scroll {
    border: 1px solid #ddd;
    border-left: none;
    border-right: none;
  }
  .text-scroll p{
    font-size: 12px;
    text-align: center;
    line-height: 30px;
  }
  .black {
    background-color: #000;
  }
  .title{
    line-height: 100px;
    text-align: center;
    color: #fff;
  }
  .animated {
    animation-duration: 1s;
    animation-fill-mode: both;
  }
  .vux-indicator.custom-bottom {
    bottom: 30px;
  }
  @-webkit-keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translate3d(0, 100%, 0);
    }
    100% {
      opacity: 1;
      transform: none;
    }
  }
  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translate3d(0, 100%, 0);
    }
    100% {
      opacity: 1;
      transform: none;
    }
  }
  .fadeInUp {
    animation-name: fadeInUp;
  }
  .swiper-demo-img img {
    width: 100%;
  }

  /*选择轮播按钮*/
  .swiper-item-click{
    position:absolute;right:0;bottom:0;

    li{
      width:10px;height:10px;background-color:$swiper-click-default;float:left;border-radius:50%;margin-right:5px;
    }

    .swiper-item-click-active{
      background-color:$swiper-click-active;
    }
  }
</style>