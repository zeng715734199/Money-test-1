<template>
  <Layout>
    <Types/>
    <Tags/>
    <Notes/>
    <NumberPad/>
  </Layout>
</template>

<script lang="ts">
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
  }
};
</script>

<style lang="scss" scoped>

</style>

