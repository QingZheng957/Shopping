<template>
<div id="home" class="wrapper">
  <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
</div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import { getHomeMultidata } from "network/home";

export default {
  name: "Home",
  components: { NavBar },
  data() {
    return {
      banners: [],
      recommends: []
    };
  },
  //从项目运行开始就要请求数据，所以用生命周期函数
  created() {
    //1.请求多个数据

    getHomeMultidata().then(res => {
      //this.result = res
      this.banners = res.data.banner;
      this.recommends = res.data.recommend;
    });
  }
};
</script>

<style>
#home {
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
</style>
