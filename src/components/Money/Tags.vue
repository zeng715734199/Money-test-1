<template>
  <div class="tags">
    <span v-for="tag in dataSource" :key="tag"
          @click="toggle(tag)"
          :class="{selected: selectedTags.indexOf(tag)>=0}">
<!--      <Icon :name="tag"/>-->
      {{ tag }}
    </span>
    <div  @click="create" class="new">
<!--      <Icon name="add"/>-->
      新增标签
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

@Component
export default class Tags extends Vue {
  @Prop() readonly dataSource: string[] | undefined;
  selectedTags: string[] = [];

  toggle(tag: string) {
    const index = this.selectedTags.indexOf(tag);
    if (index >= 0) {
      this.selectedTags.splice(index, 1);
    } else {
      this.selectedTags.push(tag);
    }
    this.$emit('update:value', this.selectedTags)
  }

  create(){
    const name = window.prompt('请输入标签名')
    if(name === ''){
      window.alert('标签名不能为空');
    }else if(this.dataSource){
        this.$emit('update:dataSource',
        [...this.dataSource, name])
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
  min-height: 55%;

  > span,.new {
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
      margin-bottom: 5px;
    }
  }
}
</style>