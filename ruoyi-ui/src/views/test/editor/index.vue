<template>
  <div id="app">
    <div class="qualityManual-container">
      <div>
        <button style="width: 120px;" type="primary" @click="getFile">测试预览office文档</button>
        <button style="width: 120px;" type="primary" @click="close">关闭</button>
      </div>
      <div v-if="show" class="qualityManual-container-office">
        <vab-only-office :option="option" />
      </div>
    </div>
  </div>
</template>

<script>
import vabOnlyOffice from '../../../components/OnlyOffice/index.vue'

export default {
  name: '',
  components: {
    vabOnlyOffice
  },
  data() {
    return {
      // 参考vabOnlyOffice组件参数配置
      option: {
        url: '',
        isEdit: '',
        fileType: '',
        title: '',
        lang: '',
        isPrint: '',
        user: { id: null, name: '' }
      },
      show: false
    }
  },
  methods: {
    getFile() {
      this.show = true
      // getAction('/file/selectById', { id: this.id }).then(res => {
      this.option.isEdit = true
      this.option.lang = 'zh-CN'
      this.option.url = 'http://119.91.213.59:8888/down/RDUwFJkecgc7.docx'
      this.option.title = '123'
      this.option.fileType = 'docx'
      this.option.isPrint = false
      this.option.user = { id: 12, name: '江亚东' }
      this.option.token = 'eGw306kukzJDM4FeL05Z'
      // })
    },
    close() {
      this.show = false
    }
  }
}
</script>

<style>
.qualityManual-container-office {
  height: 200px;
}
</style>
