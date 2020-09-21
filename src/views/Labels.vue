<template>
  <Layout>
    <div class="tags">
      <router-link class="tag" v-for="tag in tags" :key="tag.id"
                   :to="`/labels/edit/${tag.id}`">
        <span>{{ tag.name }}</span>
        <Icon name="right"/>
      </router-link>
    </div>
    <div class="createTag-wrapper">
      <Button class="createTag" @click="createTag">新建标签</Button>
    </div>
  </Layout>
</template>

<script lang="ts">

import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import Button from '@/components/Button.vue';

@Component({
  components: {Button},
})
export default class Labels extends Vue {
  get tags(){
    return this.$store.state.tagList;

  }
  beforeCreate() {
    this.$store.commit('fetchTags');
  }

  createTag() {
    const name = window.prompt('请输入标签名');
    if (!name) {
      return window.alert('标签名不能为空');
    }
    this.$store.commit('createTag', name);
  }
}
</script>

<style lang="scss" scoped>
.tags {
  background: white;
  font-size: 16px;

  > .tag {
    min-height: 44px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0 15px;
    border-bottom: 1px solid #e6e6e6;

    svg {
      color: #666;
      width: 16px;
      height: 14px;
    }
  }
}

.createTag {
  background: #28c172;
  color: #fff;
  border-radius: 4px;
  height: 40px;
  padding: 0 16px;
  border: none;

  &-wrapper {
    text-align: center;
    padding: 16px;
    margin-top: 28px;
  }
}
</style>