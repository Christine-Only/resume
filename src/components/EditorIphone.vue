<template>
  <div class="iphone">
    <h2>{{title}}</h2>
    <hr>
    <el-form :model="iphone" label-width="80px" :label-position="labelPosition" class="infoForm">
      <el-form-item label="手机">
        <el-input v-model="iphone.iphone"></el-input>
      </el-form-item>
      <el-form-item label="邮箱">
        <el-input v-model="iphone.email"></el-input>
      </el-form-item>
      <el-form-item label="微信">
        <el-input v-model="iphone.weixin"></el-input>
      </el-form-item>
      <el-form-item label="gitHub">
        <el-input v-model="iphone.gitHub"></el-input>
      </el-form-item>
      <el-form-item label="家庭住址">
        <el-input v-model="iphone.address"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'EditorIphone',
  props: ['title', 'iphone', 'labelPosition']
}
</script>

<style lang="less" scoped>
.iphone {
  h2 {
    letter-spacing: 8px;
    color: #44536a;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 8px;
  }
  hr {
    height: 3px;
    background-color: #acb1b9;
    border: none;
    margin-bottom: 8px;
  }
}
</style>
