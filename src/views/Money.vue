<template>
  <Layout class-prefix="layout">
    <Types :value.sync="record.type"/>
    <Tags :data-source.sync="tags" @update:value="onUpdateTags"/>
    <Notes @update:value="onUpdateNotes"/>
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord"/>
  </Layout>
</template>

<script lang="ts">
import Vue from 'vue';
import Types from '@/components/Money/Types.vue';
import Tags from '@/components/Money/Tags.vue';
import Notes from '@/components/Money/Notes.vue';
import NumberPad from '@/components/Money/NumberPad.vue';
import {Component, Watch} from 'vue-property-decorator';

type Record = {
  tags: string[]
  notes: string
  type: string
  amount: number
}

@Component({
  components: {Types, Tags, Notes, NumberPad}
})
export default class Money extends Vue {
  tags = ['服饰', '餐饮', '租房', '交通', '医疗',
    '娱乐', '数码', '日用', '母婴', '购物',
    '零食', '旅游'];
  recordList: Record[] = [];
  record: Record = {
    tags: [], notes: '', type: '-', amount: 0
  };

  onUpdateTags(value: string[]){
    this.record.tags = value
  };
  onUpdateNotes(value: string){
    this.record.notes = value
  };
  onUpdateAmount(value: string){
    this.record.amount = parseFloat(value)
  };
  saveRecord(){
    const record2 = JSON.parse(JSON.stringify(this.record))
    this.recordList.push(record2)
    console.log(this.recordList)
  };
  @Watch('recordList')
  onRecordListChange(){
    window.localStorage.setItem('recordList', JSON.stringify(this.recordList))
  }
};
</script>

<style lang="scss" scoped>

</style>

