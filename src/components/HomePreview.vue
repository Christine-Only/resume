<template>
  <div class="preview">
    <div class="top">
      <div class="left">
        <p>{{'姓名： '+ (resume.info.name || '请填写姓名')}}</p>
        <p>{{'年龄： '+ (resume.info.age || '请填写年龄')}}</p>
        <p>{{'所在城市： '+ (resume.info.city || '请填写所在城市')}}</p>
        <p>{{'应聘岗位： '+ (resume.info.work || '请填写应聘岗位')}}</p>
      </div>
      <div class="middle">
        <svg class="icon icon-people" aria-hidden="true">
          <use xlink:href="#icon-people"></use>
        </svg>
      </div>
      <div class="right">
        <p>{{'手机： '+ (resume.iphone.iphone || '请填写手机号')}}</p>
        <p>{{'邮箱： '+ (resume.iphone.email || '请填写邮箱')}}</p>
        <p>{{'微信： '+ (resume.iphone.weixin || '请填写微信')}}</p>
        <p>{{'gitHub： '+ (resume.iphone.gitHub || '请填写gitHub地址')}}</p>
        <p>{{'地址： '+ (resume.iphone.address || '请填写地址')}}</p>
      </div>
    </div>
    <div class="bottom">
      <section v-if="filter(resume.education).length>0">
        <!-- {{fiter(resume.object)}} 只要input输入框没填写内容，就不显示 -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-icon_fabu"></use>
        </svg>
        <h2>教育经历</h2>
        <ul>
          <li v-for="education in filter(resume.education)" :key="education.id">
            <span>{{education.school}}</span>
            <span>{{education.timeline}}</span>
            <span>{{education.major}}</span>
            <span>{{education.degree}}</span>
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.project).length>0">
        <!-- {{fiter(resume.object)}} 只要input输入框没填写内容，就不显示 -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-icon_fabu"></use>
        </svg>
        <h2>工作经历</h2>
        <ul>
          <li v-for="project in filter(resume.project)" :key="project.id">
            <span>{{project.company}}</span>
            <span>{{project.time}}</span>
            <span>{{project.workContent}}</span>
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.work).length>0">
        <!-- {{fiter(resume.object)}} 只要input输入框没填写内容，就不显示 -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-icon_fabu"></use>
        </svg>
        <h2>项目经历</h2>
        <ul>
          <li v-for="work in filter(resume.work)" :key="work.id">
            <span>{{work.workName}}</span>
            <span>{{work.time}}</span>
            <span>{{work.content}}</span>
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.award).length>0">
        <!-- {{fiter(resume.object)}} 只要input输入框没填写内容，就不显示 -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-icon_fabu"></use>
        </svg>
        <h2>获奖经历</h2>
        <ul>
          <li v-for="award in filter(resume.award)" :key="award.id">
            <span>{{award.awardName}}</span>
            <span>{{award.awardTime}}</span>
          </li>
        </ul>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePreview',
  props: ['resume'],
  methods: {
    filter (array) {
      return array.filter(item => !this.isEmpty(item))
    },
    isEmpty (object) {
      let empty = true
      for (let key in object) {
        if (object[key]) {
          empty = false
          break
        }
      }
      return empty
    }
  }
}
</script>

<style lang="less" scoped>
  .icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }
  .preview {
    background: url('../../static/backgroundpic.png') no-repeat;
    background-size: cover;
    .top {
      height: 200px;
      padding: 48px;
      background-color: transparent;
      display: flex;
      justify-content: space-between;
      align-items: center;
      .left {
        width: 200px;
        position: relative;
        left: 25px;
        p {
          margin-bottom: 8px;
          font-size: 14px;
        }
      }
    }
    .middle {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      background-color: #b0b0b0;
      position: relative;
      .icon-people {
        font-size: 96px;
        font-weight: bold;
        position: absolute;
        left: 26px;
        top: 18px;
        fill: #fff;
      }
    }
    .right {
      width: 200px;
      position: relative;
      right: 20px;
    }
    p {
      margin-bottom: 8px;
      font-size: 14px;
    }
    .bottom {
      height: 100%;
      padding: 32px 0 700px 78px;
      background-color: rgba(88, 183, 255, .6);
      section {
        display: block;
        margin-bottom: 12px;
        .icon {
          font-size: 32px;
          font-weight: bold;
        }
        h2 {
          color: #44536A;
          font-size: 20px;
          margin-bottom: 8px;
          display: inline-block;
          vertical-align: middle;
          padding-left: 16px;
        }
        ul {
          margin-bottom: 8px;
          span {
            display: inline-block;
            margin-right: 16px;
            font-size: 18px;
            margin-bottom: 4px;
            color: #fff;
          }
        }
      }
    }
  }
</style>
