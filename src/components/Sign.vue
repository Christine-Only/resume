<template>
  <div class="wrapper">
    <form @submit.prevent="signIn" v-if="actionType=='login'">
      <div class="row">
        <label>用户名</label>
        <input class="iphone" type="text" placeholder="请输入手机号" v-model="formData.username">
      </div>
      <div class="row">
        <label>密码</label>
        <input class="password" type="password" placeholder="请输入密码" v-model="formData.password">
      </div>
      <div class="actions">
        <el-button round native-type="submit">点击登录</el-button>
        <span>{{errorMessage}}</span>
      </div>
    </form>
    <form @submit.prevent="signUp" v-if="actionType=='signUp'">
      <div class="row">
        <label>用户名</label>
        <input class="iphone" type="text" placeholder="请输入手机号" v-model="formData.username">
      </div>
      <div class="row">
        <label>密码</label>
        <input class="password" type="password" placeholder="请输入密码" v-model="formData.password">
      </div>
      <div class="actions">
        <el-button round native-type="submit">点击注册</el-button>
        <span>{{errorMessage}}</span>
      </div>
    </form>
    <div class="toggle">
        <input type="radio" name="type" value="signUp" v-model="actionType">
        <span class="label">注册</span>
    </div>
    <div class="toggle">
        <input type="radio" name="type" value="login" v-model="actionType">
        <span class="label">登录</span>
    </div>
  </div>
</template>

<script>
import getErrorMessage from '../lib/getErrorMessage'
import AV from '../lib/leancloud'
import getAVUser from '../lib/getAVUser'
export default {
  name: 'Sign',
  data () {
    return {
      actionType: 'login',
      formData: {
        username: '',
        password: ''
      },
      errorMessage: ''
    }
  },
  methods: {
    signIn () {
      let {username, password} = this.formData
      AV.User.logIn(username, password).then(() => {
        this.$emit('success', getAVUser())
      }, (error) => {
        this.errorMessage = getErrorMessage(error)
      })
    },
    signUp () {
      let {username, password} = this.formData
      var user = new AV.User()
      user.setUsername(username)
      user.setPassword(password)
      user.signUp().then(() => {
        this.$emit('success', getAVUser())
      }, (error) => {
        this.errorMessage = getErrorMessage(error)
      })
    }
  }
}
</script>

<style lang="less" scoped>
.wrapper {
  margin: 30px 30px;
  .row {
    margin-bottom: 20px;
    font-size: 20px;
    margin-left: 20px;
    label {
      letter-spacing: 1px;
    }
    .iphone {
      margin-left: 10px;
    }
    .password {
      margin-left: 30px;
    }
  }
  .actions {
    width: 104px;
    margin: 0 auto;
  }
  .toggle {
    margin-left: 60px;
    margin-top: 20px;
    .register {
      margin-right: 64px;
    }
  }
}
</style>
