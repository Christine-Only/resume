<template>
  <div class="project">
    <h2>{{title}}</h2>
    <el-form label-width="80px" :label-position="labelPosition">
      <div class="work" v-for="(item,index) in project" :key="item.id">
        <hr>
        <i class="el-icon-delete" @click="handleClickDelete(index)"></i>
        <el-form-item label="公司">
          <el-input v-model="item.company"></el-input>
        </el-form-item>
        <el-form-item label="工作时间">
          <el-input v-model="item.time"></el-input>
        </el-form-item>
        <el-form-item label="工作内容">
          <el-input v-model="item.workContent"></el-input>
        </el-form-item>
        <el-button type="primary" size="small" @click="handleClickAdd()">添加</el-button>
      </div>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'EditorProject',
  props: ['title', 'labelPosition', 'project'],
  methods: {
    handleClickAdd () {
      this.project.push({company: '', time: '', workContent: ''})
    },
    handleClickDelete (index) {
      this.project.splice(index, 1)
    }
  }
}
</script>

<style lang="less" scoped>
  .project {
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
    .work {
      margin-bottom: 24px;
      position: relative;
      .el-icon-delete {
        font-size: 24px;
        color: #58B7FF;
        cursor: pointer;
        position: absolute;
        top: 10px;
        right: 0;
      }
    }
  }
</style>
