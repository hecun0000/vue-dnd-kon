<template>
  <div class="app-main">
    <header class="app-header">我大轻音还能再战五百年！！！</header>
    <div class="app-container">
      <router-view/>
    </div>
  </div>
</template>

<script>
export default {
  name: "layout"
};
</script>

<style lang="scss" scoped>
.app-main {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: #f7f7f7;
  .app-header {
    height: 80px;
    line-height: 80px;
    border-bottom: 1px solid #eee;
    text-align: center;
    font-size: 24px;
    font-weight: 700;
    color: #fff;
    background: linear-gradient(
      to right,
      #514a9d,
      #24c6dc
    ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  }
  .app-container {
    flex: 1;
    margin: 20px 50px 0;
  }
}
</style>
