<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home{
  width: 10rem;
  margin: 0 auto;
}
.home_header{
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
}
.header{
  padding-left: 74px;
  padding-top: 12px;
  padding-bottom: 12px;
  padding-right: 12px;
  background-image: url('../../static/logo_small.png');
  background-repeat: no-repeat;
  background-size: 54px 40px;
  background-position: 9px center;
  background-color: #FE5400;
}
.search_placeholder{
  width: 100%;
  box-sizing: border-box;
  background-color: #B52600;
  text-align: center;
  border-radius: 8px;
}
.search_placeholder span{
  height: 50px;
  line-height: 50px;
  font-size: 26px;
  color: #fff;
}
.carousel{
  width: 100%;
  height: 3.125rem;
  overflow: hidden;
  margin: 0 auto;
  position: relative;
}
.clearfix {
    content: '';
    clear: both;
    display: block;
}
.slide{
  width: 100%;
  height: 100%;
}
.carousel li{
  width: 100%;
  height: 100%;
  position: absolute;
}
.carousel li img{
  width: 100%;
  height: 100%;
  display: block;
}
.bullet{
  position: absolute;
  right: 10px;
  bottom: 10px;
}
.bullet span{
  display: inline-block;
  margin-right: 12px;
  width: 12px;
  height: 12px;
  background: rgba(255,255,255,0.5);
  border: 1px solid #ccc;
  border-radius: 12px;
}
.bullet .active{
  background: rgba(255,0,0,0.7);
}
.image-enter-active {
    transform: translateX(0);
    transition: all 1s ease;
}
.image-leave-active {
    transform: translateX(-100%);
    transition: all 1s ease;
}
.image-enter {
    transform: translateX(100%)
}
.image-leave {
    transform: translateX(0)
}
</style>

<template>
  <div class="home">
    <header class="home_header">
      <div class="header">
        <router-link to="/">
          <div class="search_placeholder">
            <span class="iconfont"><i>&#xe62c;</i> 寻找宝贝店铺</span>
          </div>
        </router-link>
      </div>
    </header>
    <div style="width: 100%;height: 73.6px;"></div>
    <div class="carousel">
      <transition-group tag="ul" class="clearfix slide" name="image">
        <li v-for="(image,index) in img" :key="index" v-show="index===mark">
          <router-link to="/"><img :src="image"  /></router-link>
        </li>
      </transition-group>
      <div class="bullet">
        <span v-for="(item,index) in img.length" :class="{'active':index===mark}" @click="change(index)" :key="index"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'home',
  data () {
    return {
      mark:0,
      img:[
        '../../static/banner1.jpg',
        '../../static/banner2.jpg',
        '../../static/banner3.jpg',
        '../../static/banner4.jpg',
      ]
    }
  },
  created(){
    this.play()
  },
  methods:{
    change(i) {
        this.mark = i
    },
    autoPlay() {
        this.mark++
            if (this.mark === 4) {
                this.mark = 0
                return
            }
    },
    play() {
        setInterval(this.autoPlay, 3000)
    }
  }
}
</script>


