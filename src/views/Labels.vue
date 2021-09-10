<template>
  <Layout>
    <div class="tags">
      <router-link class="tag"
                   v-for="tag in tags" :key="tag.id"
                   :to="`/labels/edit/${tag.id}`">
        <span>{{ tag.name }}</span>
        <Icon name="Right"/>
      </router-link>
    </div>
    <div class="createTag-wrapper">
      <Button class="createTag"
              @click="createTag">
        新建标签
      </Button>
    </div>
  </Layout>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import Button from '@/components/Button.vue';
import store from '@/store/index2';

@Component({
  components: {Button}
})
export default class Labels extends Vue {
  tags = store.tagList;

  createTag() {
    const name = window.prompt('请输入标签名：');
    if (name) {
      store.createTag(name);
    }
  }
}
</script>

<style lang="scss" scoped>
.tags {
  background: #fefffe;
  font-size: 18px;
  padding-left: 16px;

  > .tag {
    min-height: 45px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 3px solid #e6e6e6;

    svg {
      width: 24px;
      height: 24px;
      color: #666;
      margin-right: 16px;
    }
  }
}

.createTag {
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