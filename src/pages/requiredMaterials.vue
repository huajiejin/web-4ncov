<style scoped>
.required-materials {
  width: 100%;
}
</style>

<template>
  <div class="required-materials">
    <PostMaterials :labels="labels" @submit="handleSubmit"></PostMaterials>
  </div>
</template>

<script>
import PostMaterials from '../components/PostMaterials.vue'
import request from '../services/request'

export default {
  name: 'required-materials',
  data() {
    return {
      // 如果required-materials和supplied-materials接口字段不一样才需要传
      // formData: {
      //   address: '',
      //   comment: '',
      //   contactorName: '',
      //   contactorPhone: '',
      //   hospitalName: '',
      //   imageUrls: [],
      //   materials: [
      //     {
      //       category: '',
      //       name: '',
      //       quantity: '',
      //       standard: ''
      //     }
      //   ]
      // },
      labels: {
        title: '物资寻求信息发布',
        materials: '所需医疗物资信息',
        contactor: '收货信息',
        hospitalName: '发布机构名称',
        contactorName: '联系人',
        contactorPhone: '联系方式',
        address: '收货地址',
        uploadTip: '点击上传物资图片（可选）'
      }
    }
  },
  methods: {
    handleSubmit(formData) {
      console.log(formData)
      request.post('/required-materials', formData).then(res => {
        console.log(res)
        // TODO：提交成功后的行为
        alert('post required-materials success')
      })
    }
  },
  components: { PostMaterials }
}
</script>
