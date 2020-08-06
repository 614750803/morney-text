<template>
  <Layout class-prefix="layout">
   <NumberPad/>
    <Types/>
   <Notes/>
   <Tags/>
  </Layout>
</template>

<script lang="ts">
import NumberPad from '@/components/Money/NumberPad.js';
import Types from '@/components/Money/Types.js';
import Notes from '@/components/Money/Notes.js';
import Tags from '@/components/Money/Tags.js';
export default {
  name: 'Money',
  components: {Tags, Notes, Types, NumberPad},
};
</script>

<style lang="scss">
.layout-content{
  display: flex;
  flex-direction: column-reverse;
}
</style>

<style lang="scss" scoped>

</style>
