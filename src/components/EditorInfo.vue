<template>
  <div class="info">
    <h2>{{title}}</h2>
    <hr>
    <el-form :model="info" label-width="80px" :label-position="labelPosition" class="infoForm">
      <el-form-item label="姓名">
        <el-input v-model="info.name"></el-input>
      </el-form-item>
      <el-form-item label="年龄">
        <el-input v-model="info.age"></el-input>
      </el-form-item>
      <el-form-item label="所在城市">
        <el-input v-model="info.city"></el-input>
      </el-form-item>
      <el-form-item label="应聘岗位">
        <el-input v-model="info.work"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'EditorInfo',
  props: ['title', 'labelPosition', 'info']
}
</script>

<style lang="less" scoped>
  .info {
    h2 {
      letter-spacing: 8px;
      color: #44536A;
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
