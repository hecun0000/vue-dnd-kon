<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="8" v-for="(o, index) in dataList" :key="index">
        <el-card :body-style="{ padding: '0px' }">
          <img :src="o.cover" class="image">
          <div style="padding: 14px;">
            <a :href="o.url" target="blank">{{ o.title }}</a>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "KonList",
  data() {
    return {
      dataList: [
        {
          url: "https://www.bilibili.com/bangumi/media/md28220978",
          title: "轻音少女 第一季",
          cover: "http://img.hecun.site/Fup3ro_Ic05ITo__SqmDR5ui3w0f"
        },
        {
          url: "https://www.bilibili.com/bangumi/media/md28220984",
          title: "轻音少女 第二季",
          cover: "http://img.hecun.site/Fu6tBbp6ixySvlEErJ0uSSrDzf6F"
        },
        {
          url: "https://www.bilibili.com/bangumi/media/md28220988",
          title: "轻音少女 剧场版",
          cover: "http://img.hecun.site/Ftbz0a22LAx0ssccqQti6l-KHmjt"
        }
      ]
    };
  }
};
</script>


<style scoped>
.image {
  width: 100%;
  display: block;
}
a {
  text-decoration: none;
}
</style>
