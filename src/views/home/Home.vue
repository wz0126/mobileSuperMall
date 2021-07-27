<template>
  <div id="home" class="wrapper">
   <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
  </div>
</template>

<script>
import NavBar from '../../components/common/navbar/NavBar.vue';
import {getHomeMultidate} from "../../network/home";
  export default {
    name: "Home",
    components: {
     NavBar 
    },
    data(){
      return {
        banners:[],
        recommends:[]
      }
    },
    created(){
      // 请求多个数据
      this.getHomeData();
    },
    methods:{
      async getHomeData(){
        this.result = await getHomeMultidate().then(res => {
        console.log(res)
        console.log(this.result)
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      })
      }
    }
  }
</script>

<style scoped>
  #home {
    /*padding-top: 44px;*/
    height: 100vh;
    position: relative;
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }

  .tab-control {
    position: sticky;
    top: 44px;
    z-index: 9;
  }

  .content {
    overflow: hidden;

    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }

  /*.content {*/
    /*height: calc(100% - 93px);*/
    /*overflow: hidden;*/
    /*margin-top: 44px;*/
  /*}*/
</style>
