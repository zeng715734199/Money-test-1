<template>
  <div>
    <label class="notes">
      <span class="name">{{this.fieldName}}</span>
      <input type="text"
             v-model="value"
             :placeholder="this.placeholder">
    </label>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop, Watch} from 'vue-property-decorator';

@Component
export default class FormItem extends Vue {
  value = '';
  @Prop({required: true}) fieldName!: string;
  @Prop() placeholder?: string
  @Watch('value')
  onUpdateNotes(value: string) {
    this.$emit('update:value', value);
  }
};
</script>

<style lang="scss" scoped>
.notes {
  font-size: 14px;
  background: #fefffe;
  padding-left: 16px;
  display: flex;
  align-items: center;
  box-shadow: 3px 3px 3px 3px #e6e6e6;

  .name {
    padding-right: 16px;
    color: #60a69b;
    font-weight: 600;
  }

  input {
    min-height: 54px;
    flex-grow: 1;
    background: transparent;
    border: none;
    padding-right: 16px;
  }
}
</style>