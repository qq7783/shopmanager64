<template>
  <!-- 最外面的卡片容器 -->
  <el-card class="box-card">
    <div class="text item">
      <!-- 面包屑导航 -->
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
        <el-breadcrumb-item>用户管理</el-breadcrumb-item>
        <el-breadcrumb-item>用户列表</el-breadcrumb-item>
      </el-breadcrumb>
      <!-- 搜索框+添加按钮 -->
      <el-row class="search">
        <el-col>
          <el-input placeholder="请输入内容" v-model="query" class="input-with-select">
            <el-button slot="append" icon="el-icon-search"></el-button>
          </el-input>
        </el-col>
      </el-row>
    </div>
  </el-card>
</template>

<script>
export default {
  data () {
    return {
      query: ""
    }
  }
};
</script>

<style>
.box-card {
  height: 100%;
}
.search {
  margin-top: 20px;
}
</style>
