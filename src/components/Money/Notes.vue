<template>
  <div>
    <label class="notes">
      <span class="name">备注:</span>
      <input type="text" placeholder="在这里输入备注">
    </label>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Notes.vue'
};
</script>

<style lang="scss" scoped>
.notes {
  font-size: 14px;
  background: rgb(254, 255, 254);
  padding-left: 16px;
  display: flex;
  align-items: center;
  .name {
    padding-right: 16px;
    color: #60a69b;
    font-weight: 600;
  }
  input {
    height: 45px;
    flex-grow: 1;
    background: transparent;
    border: none;
    padding-right: 16px;
  }
}
</style>