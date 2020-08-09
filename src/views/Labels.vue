<template>
  <Layout>
    <ul class="tags">
      <li v-for="tag in tags" :key="tag">
        <span>{{ tag }}</span>
        <Icon name="right"/>
      </li>
    </ul>
    <div class="createTag-wrapper">
      <button class="createTag" @click="createTag">新建标签</button>
    </div>
  </Layout>
</template>

<script lang="ts">

import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import tagListModel from '@/models/tagListModel';

tagListModel.fetch();

@Component
export default class Labels extends Vue {
  tags = tagListModel.data;

  createTag() {
    const name = window.prompt('请输入标签名');
    if (name) {
        const message = tagListModel.create(name);
        if (message === 'duplicated') {
          window.alert('标签名重复');
        }else if(message === 'success'){
          window.alert('添加成功')
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
.tags {
  background: white;
  font-size: 16px;

  > li {
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
  background: #767676;
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