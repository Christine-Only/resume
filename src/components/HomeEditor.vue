<template>
  <div class="editor">
    <ul class="left">
      <li v-for="i in items" :key="i.id" :class="{active:currentTab === i}" @click="currentTab = i">
        <svg class="icon">
          <use :xlink:href="`#icon-${icons[i]}`"></use>
        </svg>
      </li>
    </ul>
    <ul class="right">
      <li :class="{hover:currentTab===0}">
        <editor-info title="个人信息" :labelPosition="resume.labelPosition" :info="resume.info"></editor-info>
      </li>
      <li :class="{hover:currentTab===1}">
        <editor-iphone title="联系方式" :labelPosition="resume.labelPosition" :iphone="resume.iphone"></editor-iphone>
      </li>
      <li :class="{hover:currentTab===2}">
        <editor-education title="教育经历" :labelPosition="resume.labelPosition" :education="resume.education"></editor-education>
      </li>
      <li :class="{hover:currentTab===3}">
        <editor-project title="工作经历" :labelPosition="resume.labelPosition" :project="resume.project"></editor-project>
      </li>
      <li :class="{hover:currentTab===4}">
        <editor-work title="项目经历" :labelPosition="resume.labelPosition" :work="resume.work"></editor-work>
      </li>
      <li :class="{hover:currentTab===5}">
        <editor-award title="获奖经历" :labelPosition="resume.labelPosition" :award="resume.award"></editor-award>
      </li>
    </ul>
  </div>
</template>

<script>
import EditorInfo from './EditorInfo'
import EditorIphone from './EditorIphone'
import EditorEducation from './EditorEducation'
import EditorProject from './EditorProject'
import EditorWork from './EditorWork'
import EditorAward from './EditorAward'
export default {
  name: 'HomeEditor',
  props: ['resume'],
  components: {
    EditorInfo,
    EditorIphone,
    EditorEducation,
    EditorProject,
    EditorWork,
    EditorAward
  },
  data () {
    return {
      currentTab: 0,
      items: [0, 1, 2, 3, 4, 5],
      icons: ['identity', 'phone', 'education', 'work1', 'xiangmu1', 'award']
    }
  }
}
</script>

<style lang="less" scoped>
  .editor {
    min-height: 100px;
    display: flex;
    .left {
      width: 64px;
      background-color: #58B7FF;
      li {
        padding: 16px;
        .icon {
          width: 32px;
          height: 32px;
          fill: #fff;
        }
      }
      .active {
        background-color: #fff;
        .icon {
          fill: #58B7FF;
        }
      }
    }
    .right {
      flex: 1;
      li {
        padding: 24px;
        display: none;
        height: 100%;
        overflow: auto;
      }
      .hover {
        display: block;
      }
    }
  }
</style>
