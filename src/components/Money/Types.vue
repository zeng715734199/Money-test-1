<template>
  <div>
    <ul class="types">
      <li :class="type === '-' && 'selected'"
          @click="selectType('-')">支出
      </li>
      <li :class="type === '+' && 'selected'"
          @click="selectType('+')">收入
      </li>
    </ul>
  </div>
</template>

<script lang="js">
export default {
  name: 'Types',
  data() {
    return {
      type: '-'  //‘-’号表示支出，'+'号表示收入
    }
  },
  methods: {
    selectType(type) {  // type只能是'-'或者'+'
      if (type !== '-' && type !== '+') {
        throw new Error('type is unknown')
      }
      this.type = type
    }
  }
}
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
    width: 20%;
    height: 36px;
    position: relative;
    border: none;
    margin-bottom: -22px;

    &.selected::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 3px;
      background: #333;
    }
  }
}
</style>
