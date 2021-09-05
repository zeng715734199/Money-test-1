<template>
  <div class="numberPad">

    <div class="buttons">
      <button class="empty"><span>清空</span></button>
      <div class="output"><span class="numb">100</span></div>
      <button><span>1</span></button>
      <button><span>2</span></button>
      <button><span>3</span></button>
      <button><span>+</span></button>
      <button><span>4</span></button>
      <button><span>5</span></button>
      <button><span>6</span></button>
      <button><span>-</span></button>
      <button><span>7</span></button>
      <button><span>8</span></button>
      <button><span>9</span></button>
      <button class="ok"><span class="huang">OK</span></button>
      <button><span>.</span></button>
      <button class="zero"><span>0</span></button>
      <button><span>删除</span></button>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'NumberPad.vue'
};
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.numberPad {
  background: $bg;

  .buttons {
    .empty {
      width: 25%
    }

    .output {
      @extend %innerShadow;
      width: 75%;
      height: 45px;
      font-size: 25px;
      font-family: Consolas, monospace;
      text-align: right;
      float: right;

      > .numb {
        padding: 4px 14px;
        display: block;
        width: 100%;
        height: 100%;
        border: 3px solid black;
        border-radius: 10px;
        background: rgb(254, 255, 254);
      }
    }

    > button {
      width: 25%;
      height: 45px;
      background: $bg;
      border: none;
      padding: 3px;

      &.ok {
        height: 45*2px;
        float: right;
      }

      > span {
        @extend %center;
        border: 3px solid black;
        border-radius: 10px;
        width: 100%;
        height: 100%;
        background: rgb(254, 255, 254);
      }

      .huang {
        background: rgb(254, 204, 2);
      }
    }
  }
}
</style>