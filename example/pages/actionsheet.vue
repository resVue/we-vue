<template>
  <div class="page page-with-padding">
    <div class="buttons">
      <wv-button type="default" @click.native="showActionsheet('ios')">iOS ActionSheet</wv-button>
      <wv-button type="default" @click.native="showActionsheet('android')">Android ActionSheet</wv-button>
    </div>

    <wv-actionsheet :type="type" :actions="actions" cancel-text="取消" v-model="sheetVisible"></wv-actionsheet>
  </div>
</template>

<script type="text/babel">
export default {
  data () {
    return {
      type: 'ios',
      sheetVisible: false,
      actions: []
    }
  },

  methods: {
    showActionsheet (type) {
      this.type = type
      this.sheetVisible = true
    },

    menuClick (key) {
      console.log(`menu ${key} clicked`)
    }
  },

  mounted () {
    this.actions = [
      {
        name: '示例菜单1',
        key: 'menu1',
        method: () => {
          this.menuClick('menu1')
        }
      },
      {
        name: '示例菜单2',
        key: 'menu2',
        method: () => {
          this.menuClick('menu2')
        }
      },
      {
        name: '示例菜单3',
        key: 'menu3',
        method: () => {
          this.menuClick('menu3')
        }
      }
    ]
  }
}
</script>

<style scoped lang="scss">
  .buttons {
    display: block;
    padding: 0 20px;
    margin: 20px auto;
  }
</style>
