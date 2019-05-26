<template>
  <el-carousel class="carousel" arrow="never">
    <el-carousel-item v-for="item in imgs" :key="item">
      <img :src="item" class="img">
    </el-carousel-item>
  </el-carousel>
</template>
<script>
export default {
  name: "carousel",
  data() {
    return {
      imgs: [
        "http://img.hecun.site/Fi_4-MXvWoH3h24N6WKSW-PM5qhb",
        "http://img.hecun.site/FoWCmHon7gFlbq8HADcN_puG3eRn",
        "http://img.hecun.site/FtppAPrJc-biePBT2WlbPCIsaw_V",
        "http://img.hecun.site/FrF0gMPcB7_NSJYoup2ZQP2ZLXhC",
        "http://img.hecun.site/Fp1FMXqUls2PRX1grjajMZSf5qKj",
        "http://img.hecun.site/Flwf5_PrKqe4s0awwSq-5_XawZ2a"
      ]
    };
  }
};
</script>
<style lang="scss" scoped>
.img {
  height: 300px;
  display: block;
  margin: 0 auto;
}
</style>

