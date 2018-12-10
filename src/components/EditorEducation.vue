<template>
  <div class="education">
    <h2>{{title}}</h2>
    <el-form label-width="80px" :label-position="labelPosition">
      <div class="work" v-for="(item,index) in education" :key="item.id">
        <hr>
        <i class="el-icon-delete" @click="handleClickDelete(index)"></i>
        <el-form-item label="毕业学校">
          <el-input v-model="item.school"></el-input>
        </el-form-item>
        <el-form-item label="毕业时间">
          <el-input v-model="item.timeline"></el-input>
        </el-form-item>
        <el-form-item label="所学专业">
          <el-input v-model="item.major"></el-input>
        </el-form-item>
        <el-form-item label="学位">
          <el-input v-model="item.degree"></el-input>
        </el-form-item>
        <el-button type="primary" size="small" @click="handleClickAdd()">添加</el-button>
      </div>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'EditorEducation',
  props: ['title', 'labelPosition', 'education'],
  methods: {
    handleClickAdd () {
      this.education.push({school: '', timeline: '', major: '', degree: ''})
    },
    handleClickDelete (index) {
      if (index > 0) {
        this.education.splice(index, 1)
      } else {
        alert('不能删除!')
      }
    }
  }
}
</script>

<style lang="less" scoped>
  .education {
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
