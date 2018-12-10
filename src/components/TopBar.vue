<template>
  <div class="topbar">
    <div class="logo">
      <i class="el-icon-menu iconcolor"></i>
      Resume
    </div>
    <div class="actions">
      <div class="userActions">
        <el-button :plain="true">注册</el-button>
        <el-button type="primary">登录</el-button>
        <el-button type="success" @click="preview">预览</el-button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Topbar',
  methods: {
    preview () {
      this.$emit('change')
    }
  }
}
</script>
<style lang="less" scoped>
  .topbar {
    display: flex;
    justify-content: space-between;
    padding: 14px;
    box-shadow: 0px 0px 3px rgba(0, 0, 0, .5);
    .logo {
      line-height: 40px;
      font-size: 21px;
      .iconcolor {
        color: #58B7FF;
        padding-right: 8px;
        font-weight: bold;
      }
    }
  }
</style>
