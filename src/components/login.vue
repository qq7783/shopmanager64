<template>
  <div class="login-wrap">
    <el-form class="login-form" label-position="top" label-width="80px" :model="formdata">
      <h2>用户登录</h2>
      <el-form-item label="用户名">
        <el-input v-model="formdata.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="formdata.password"></el-input>
      </el-form-item>
      <el-button @click.prevent="handleLogin()" class="login-btn" type="success">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formdata: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    // 登录请求
    async handleLogin() {
      const res = await this.$http.post(`login`, this.formdata);
      // console.log(res);
      const {
        data: {
          data,
          meta:{msg, status}
        }
      } = res;
      if (status === 200) {
        // 存储token
        localStorage.setItem("token",data.token); //h5新特性本地存储
        // 渲染home组件 改标识
        this.$router.push({
          name: "home"
        });
        return;
      };
      this.$message.error(msg);
    }
  }
};
</script>

<style>
.login-wrap {
  /* 注意: 百分比布局 父元素height:100% */
  height: 100%;
  background-color: #324152;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login-form {
  background-color: #ffffff;
  border-radius: 5px;

  width: 400px;
  padding: 30px;
}
.login-btn {
  width: 100%;
}
</style>
