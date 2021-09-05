<template>
  <div class="tags">
    <span>
      <Icon name="餐饮"/>
      餐饮
    </span>
    <span>
    <Icon name="交通"/>
    </span>
    <span>
    <Icon name="医疗"/>
    </span>
    <span>
    <Icon name="娱乐"/>
    </span>
    <span>
    <Icon name="数码"/>
    </span>
    <span>
    <Icon name="服饰"/>
    </span>
    <div class="new">
      <button>新增标签</button>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Tags.vue'
};
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";
.tags {
  display: flex;
  flex-grow: 1;
  font-size: 14px;
  padding: 20px;
  background: rgb(246, 247, 242);
  align-content: flex-start;
  flex-wrap: wrap;

  > span > .icon {
    width: 50px;
    height: 50px;
  }

  span {
    @extend %center;
    margin: 10px 20px;
    padding: 5px 15px;
    flex-direction: column;
    border:1px solid black;
  }
  > .new {
    padding-top: 16px;
    button {
      background: transparent;
      border: none;
      color: #999;
      border-bottom: 1px solid;
      padding: 0 4px;
    }
  }
}
</style>