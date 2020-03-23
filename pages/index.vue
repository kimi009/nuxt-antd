<template>
  <div class="page-index">
    <a-menu v-model="current" mode="horizontal" theme="dark">
      <a-menu-item key="mail">
        <a-icon type="mail" />Navigation One
      </a-menu-item>
      <a-menu-item key="app">
        <a-icon type="appstore" />Navigation Two
      </a-menu-item>
      <a-sub-menu>
        <span slot="title" class="submenu-title-wrapper"
          ><a-icon type="setting" />Navigation Three - Submenu</span
        >
        <a-menu-item-group title="Item 1">
          <a-menu-item key="setting:1">Option 1</a-menu-item>
          <a-menu-item key="setting:2">Option 2</a-menu-item>
        </a-menu-item-group>
        <a-menu-item-group title="Item 2">
          <a-menu-item key="setting:3">Option 3</a-menu-item>
          <a-menu-item key="setting:4">Option 4</a-menu-item>
        </a-menu-item-group>
      </a-sub-menu>
      <a-menu-item key="alipay">
        <a href="https://antdv.com" target="_blank" rel="noopener noreferrer"
          >Navigation Four - Link</a
        >
      </a-menu-item>
    </a-menu>
    <a-row :gutter="16">
      <template v-for="item in list">
        <a-col :key="item.id" :span="8">
          <a-card :title="item.name" :bordered="false">
            <p>{{ item.des }}</p>
          </a-card>
        </a-col>
      </template>
    </a-row>
    <a-row type="flex" justify="center">
      <a-col
        ><a-button type="primary" @click="toDetail"
          >测试页面跳转渲染情况</a-button
        ></a-col
      >
    </a-row>
  </div>
</template>

<script>
export default {
  components: {},
  async asyncData({ $axios }) {
    const {
      status,
      data: { list }
    } = await $axios.get('/user/info')
    if (status === 200) {
      return { list }
    }
    return { list: [] }
  },
  data() {
    return {
      current: ['mail']
    }
  },
  methods: {
    toDetail() {
      location.href = '/users/111'
    }
  }
}
</script>
