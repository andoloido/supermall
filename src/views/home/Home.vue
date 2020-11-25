<template>
  <div id="home">
    <nav-bar class="home-nav"> <div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners" />
    <home-recommend-view :recommendList="recommendList" />
  </div>
</template>

<script>
import { getHomeMultidata } from "network/home";

import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "../home/childComps/HomeSwiper";
import HomeRecommendView from "./childComps/HomeRecommendView.vue";

export default {
  components: { NavBar, HomeSwiper, HomeRecommendView },
  name: "Home",
  data() {
    return {
      banners: [],
      recommendList: [],
    };
  },
  created() {
    getHomeMultidata().then((res) => {
      console.log(res);
      this.banners = res.data.banner.list;
      this.recommendList = res.data.recommend.list;
    });
  },
};
</script>

<style scoped>
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
</style>