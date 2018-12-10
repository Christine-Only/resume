<template>
  <div class="login">
    <div class="dialog">
      <header class="header">
        <h1>在线简历编辑器</h1>
      </header>
      <main>
        <slot></slot>
      </main>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login'
}
</script>
<style lang="less" scoped>
.login {
  position: fixed;
  top: 50%;
  left: 50%;
  margin-top: -175px;
  margin-left: -200px;
  .dialog {
    box-shadow: 0px 0px 15px #9a9494;
    background: #a9a9ab;
    height: 350px;
    width: 400px;
    border-radius: 10px;
    .header {
      font-size: 26px;
      text-align: center;
      h1 {
        padding-top: 25px;
        font-weight: bold;
        color: #444;
      }
    }
  }
}
</style>
