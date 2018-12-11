<template>
  <div id="app" :class="{exitControl: previewMode}">
    <top-bar class="topbar" @change="change"></top-bar>
    <main class="main">
      <home-editor class="editor" :resume="resume"></home-editor>
      <home-preview class="preview" :resume="resume"></home-preview>
    </main>
    <el-button @click="exitPreview" id="exit" type="danger">退出预览</el-button>
  </div>
</template>

<script>
import './assets/reset.css'
import TopBar from './components/Topbar'
import HomeEditor from './components/HomeEditor'
import HomePreview from './components/HomePreview'
export default {
  name: 'App',
  components: {
    TopBar,
    HomeEditor,
    HomePreview
  },
  data () {
    return {
      previewMode: false,
      resume: {
        labelPosition: 'top',
        info: {name: '', age: '', city: '', work: ''},
        iphone: {iphone: '', email: '', weixin: '', gitHub: '', address: ''},
        education: [{school: '', timeline: '', major: '', degree: ''}],
        project: [{company: '', time: '', workContent: ''}],
        work: [{workName: '', time: '', content: ''}],
        award: [{awardName: '', awardTime: ''}]
      }
    }
  },
  methods: {
    change () {
      this.previewMode = true
    },
    exitPreview () {
      this.previewMode = false
    }
  }
}
</script>

<style lang="less" scoped>
  #app {
    .main {
      display: flex;
      // height: 100%;
      background-color: #F9FAFC;
      .editor{
        width: 500px;
        margin: 16px 8px 16px 16px;
        background-color: #fff;
        box-shadow: 0 0 3px rgba(0, 0, 0, .3);
        border-radius: 4px;
        overflow: auto;
        .icon {
          width: 1em; height: 1em;
          vertical-align: -0.15em;
          fill: currentColor;
          overflow: hidden;
        }
      }
      .preview {
        flex: 1;//让所有弹性盒子对象的子元素都有相同的长度
        box-shadow: 0 0 3px rgba(0, 0, 0, .3);
        border-radius: 4px;
        background-color: #fff;
        margin: 16px 16px 16px 8px;
        overflow: auto;
      }
    }
  }
  #exit {
    display: none;
  }
  .exitControl {
    .topbar {
      display: none;
    }
    .editor {
      display: none;
    }
    .preview {
      max-width: 800px;
      margin: 32px auto 0px !important;
    }
    #exit {
      position: fixed;
      display: inline-block;
      bottom: 8px;
      right: 8px;
    }
  }
</style>
