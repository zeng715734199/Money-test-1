<template>
  <div id="app">
    <router-view/>
    <hr/>
  </div>
</template>

<style lang="scss">
@import "~@/assets/style/helper.scss";
@import "~@/assets/style/reset.scss";

body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #333;
  line-height: 1.5;
  font-family: $font-hei;
  font-size: 16px;
  background: rgb(246, 247, 242);
}
body::-webkit-scrollbar {
  display:none
}
</style>
