<template>
  <Layout>
    <Types/>
    <Tags :data-source="tags"/>
    <Notes/>
    <NumberPad/>
  </Layout>
</template>

<script>
import Types from '@/components/Money/Types.vue';
import Tags from '@/components/Money/Tags.vue';
import Notes from '@/components/Money/Notes.vue';
import NumberPad from '@/components/Money/NumberPad.vue';
export default {
  name: 'Money',
  components: {
    Types,
    Tags,
    Notes,
    NumberPad,
  },
  data(){
    return{
      tags: ['服饰', '餐饮', '租房', '交通', '医疗',
             '娱乐', '数码', '日用', '母婴', '购物',
             '零食', '旅游']
    }
  }
};
</script>

<style lang="scss" scoped>

</style>

