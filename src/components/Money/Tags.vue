<template>
  <div class="tags">
    <ul>
      <li v-for="tag in tagList" :key="tag.id"
          @click="toggle(tag)"
          :class="{selected: selectedTags.indexOf(tag)>=0}">
        {{ tag.name }}
      </li>
      <li @click="createTag" class="new">
        新增标签
        <!--      <Icon name="add"/>-->
      </li>
    </ul>



  </div>
</template>

<script lang="ts">
import {Component} from 'vue-property-decorator';
import {mixins} from 'vue-class-component';
import TagHelper from '@/mixins/TagHelper.ts';

@Component
export default class Tags extends mixins(TagHelper) {
  selectedTags: string[] = [];

  get tagList() {
    return this.$store.state.tagList;
  }

  created() {
    this.$store.commit('fetchTags');
  }

  toggle(tag: string) {
    const index = this.selectedTags.indexOf(tag);
    if (index >= 0) {
      this.selectedTags.splice(index, 1);
    } else {
      this.selectedTags.push(tag);
    }
    this.$emit('update:value', this.selectedTags);
  }
};
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.tags {
  padding: 20px;
  min-height: 54vh;
  > ul {
    display: flex;
    align-content: flex-start;
    flex-wrap: wrap;
    flex-grow: 1;

    > li {
      @extend %center;
      margin: 5px;
      padding: 3px 10px;
      font-size: 16px;
      font-weight: 600;
      border: 3px solid #000;
      border-radius: 8px;
      background: #fefffe;

      &.new {
        background: #f2a39f;
      }

      &.selected {
        background: rgb(200, 226, 216);
        border: 3px solid $bg;
      }

      > .icon {
        min-width: 30px;
        min-height: 30px;
        margin-bottom: 5px;
      }
    }
  }
}
</style>