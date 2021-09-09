<template>
  <Layout class-prefix="layout">
    <Types :value.sync="record.type"/>
    <Tags :data-source.sync="tags" @update:value="onUpdateTags"/>
    <FormItem field-name="备注："
              placeholder="在这里输入备注"
              @update:value="onUpdateNotes"/>
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord"/>
  </Layout>
</template>

<script lang="ts">
import Vue from 'vue';
import Types from '@/components/Money/Types.vue';
import Tags from '@/components/Money/Tags.vue';
import FormItem from '@/components/Money/FormItem.vue';
import NumberPad from '@/components/Money/NumberPad.vue';
import {Component} from 'vue-property-decorator';


@Component({
  components: {FormItem, Types, Tags, FormItem, NumberPad}
})
export default class Money extends Vue {
  tags = window.tagList;
  recordList = window.recordList;
  record: RecordItem = {
    tags: [], notes: '', type: '-', amount: 0
  };

  onUpdateTags(value: string[]) {
    this.record.tags = value;
  };

  onUpdateNotes(value: string) {
    this.record.notes = value;
  };

  onUpdateAmount(value: string) {
    this.record.amount = parseFloat(value);
  };

  saveRecord() {
    window.createRecord(this.record);
  };
};
</script>

<style lang="scss" scoped>

</style>

