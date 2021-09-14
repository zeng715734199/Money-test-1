<template>
  <ul class="tabs" :class="{[classPrefix+'-tabs']: classPrefix}">
    <li v-for="item in dataSource" :key="item.value" class="tabs-item"
        :class="liClass(item)" @click="select(item)">
      {{ item.text }}
    </li>
  </ul>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

type DataSourceItem = { text: string, value: string }

@Component
export default class Tabs extends Vue {
  @Prop({required: true, type: Array})
  dataSource!: DataSourceItem[];
  @Prop(String)
  readonly value!: string;
  @Prop(String)
  classPrefix?: string;

  liClass(item: DataSourceItem) {
    return {
      [this.classPrefix + '-tab-item']: this.classPrefix,
      selected: item.value === this.value
    }
  }
  select(item: DataSourceItem) {
    this.$emit('update:value', item.value)
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.tabs {
  @extend %center;
  background: $bg;
  text-align: center;
  font-size: 18px;
  font-weight: 600;
  min-height: 48px;

  &-item {
    @extend %center;
    width: 20%;
    min-height: 38px;
    position: relative;
    margin-bottom: -15px;

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