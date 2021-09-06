<template>
  <div class="tags">
    <span v-for="tag in dataSource" :key="tag"
          @click="toggle(tag)"
          :class="{selected: selectedTags.indexOf(tag)>=0}">
      <Icon :name="tag"/>
      {{ tag }}
    </span>
    <div class="new">
      <button>新增标签</button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

@Component
export default class Tags extends Vue {
  @Prop() dataSource: string[] | undefined;
  selectedTags: string[] = [];

  toggle(tag: string) {
    const index = this.selectedTags.indexOf(tag);
    if (index >= 0) {
      this.selectedTags.splice(index, 1);
    } else {
      this.selectedTags.push(tag);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.tags {
  display: flex;
  flex-grow: 1;
  padding: 20px;
  background: rgb(246, 247, 242);
  align-content: flex-start;
  flex-wrap: wrap;

  > span {
    @extend %center;
    margin: 5px;
    padding: 8px;
    flex-direction: column;
    border: 3px solid transparent;
    font-size: 12px;
    font-weight: 600;

    &.selected {
      background: rgb(200, 226, 216);
      border: 3px solid $bg;
    }

    > .icon {
      min-width: 30px;
      min-height: 30px;
    }
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