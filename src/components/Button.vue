<template>
  <button class="button"
          @click="$emit('click', $event)">
    <slot/>
  </button>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator';

@Component
export default class Button extends Vue {

}
</script>

<style lang="scss" scoped>
.button {
  background: rgb(254, 204, 2);
  font-weight: 600;
  font-size: 18px;
  border: 3px solid #000;
  border-radius: 8px;
  padding: 8px 16px;

  &-wrapper {
    text-align: center;
    padding: 16px;
    margin-top: 44 - 16px;
  }
}
</style>