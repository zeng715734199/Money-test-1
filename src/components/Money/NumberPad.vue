<template>
  <div class="numberPad">

    <div class="buttons">
      <button @click="clear" class="empty"><span>清空</span></button>
      <div class="output"><span class="numb">{{ output }}</span></div>
      <button @click="outputContent"><span>1</span></button>
      <button @click="outputContent"><span>2</span></button>
      <button @click="outputContent"><span>3</span></button>
      <button @click="ok" class="ok"><span class="finish">OK</span></button>
      <button @click="outputContent"><span>4</span></button>
      <button @click="outputContent"><span>5</span></button>
      <button @click="outputContent"><span>6</span></button>
      <button @click="outputContent"><span>7</span></button>
      <button @click="outputContent"><span>8</span></button>
      <button @click="outputContent"><span>9</span></button>
      <button @click="outputContent"><span>.</span></button>
      <button @click="outputContent" class="zero"><span>0</span></button>
      <button @click="remove"><span>删除</span></button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator';

@Component
export default class NumberPad extends Vue {
  output: string = '0';

  outputContent(event: MouseEvent) {
    const button = (event.target as HTMLButtonElement);
    const input = button.textContent!;
    if (this.output.length === 16) {return;}
    if (this.output === '0') {
      if ('0123456789'.indexOf(input) >= 0) {
        this.output = input;
      } else {
        this.output += input;
      }
      return;
    }
    if (this.output.indexOf('.') >= 0 && input === '.') {return;}
    this.output += input;
  };

  remove() {
    if (this.output.length === 1) {
      this.output = '0';
    } else {
      this.output = this.output.slice(0, -1);
    }
  };

  clear() {
    this.output = '0';
  };

  ok() {
    this.$emit('update:value', this.output)
  };
}
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
        height: 45*4px;
        font-size: 24px;
        float: right;
        font-weight: 700;
      }

      > span {
        @extend %center;
        border: 3px solid black;
        border-radius: 10px;
        width: 100%;
        height: 100%;
        background: rgb(254, 255, 254);
      }

      .finish {
        background: rgb(254, 204, 2);
      }
    }
  }
}
</style>