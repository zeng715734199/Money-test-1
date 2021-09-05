<template>
  <div>
    <ul class="types">
      <li class="chose" active-class="selected">支出</li>
      <li active-class="selected">收入</li>
    </ul>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Types'
};
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.types {
  @extend %center;
  background: $bg;
  text-align: center;
  font-size: 16px;
  font-weight: 500;
  min-height: 60px;

  > li {
    @extend %center;
    @extend %outerShadow;
    border: 3px solid #000;
    border-radius: 8px;
    background: rgb(254, 255, 254);
    width: 20%;
    height: 36px;
    position: relative;
    margin-left: 5px;
  }
}
</style>
