<template>
  <div class="award">
    <h2>{{title}}</h2>
    <el-form label-width="80px" :label-position="labelPosition">
      <div class="jingli" v-for="(item,index) in award" :key="item.id">
        <hr>
        <i class="el-icon-delete" @click="handleClickDelete(index)"></i>
        <el-form-item label="项目经历">
          <el-input v-model="item.awardName"></el-input>
        </el-form-item>
        <el-form-item label="项目时间">
          <el-input v-model="item.awardTime"></el-input>
        </el-form-item>
        <el-button type="primary" size="small" @click="handleClickAdd()">添加</el-button>
      </div>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'EditorWork',
  props: ['title', 'labelPosition', 'award'],
  methods: {
    handleClickAdd () {
      this.work.push({awardName: '', awardTime: ''})
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
  .award {
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
    .jingli {
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
