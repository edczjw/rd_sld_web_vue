<template>
  <div class="login">
    <h2>民盛赎楼贷信息平台</h2>
    <p class="phone">遇到问题 ? 可拨打客服电话：010-123456221</p>

    <el-card class="box-card">
      <div class="tit">登录</div>
      <div class="insert">
        <el-form
          :model="setForm"
          status-icon
          ref="setForm"
          label-width="70px"
          class="demo-ruleForm"
        >
          <el-form-item label="账号" prop="phone" :rules="rules.phone">
            <el-input v-model.trim="setForm.phone" auto-complete="off"></el-input>
          </el-form-item>

          <el-form-item label="密码" prop="password" :rules="rules.kong">
            <el-input type="password" v-model.trim="setForm.password"></el-input>
          </el-form-item>
        </el-form>
        <div class="button">
          <el-button type="text" class="forgetbtn" @click="register">立即注册</el-button>
        </div>
        <div class="but" @click="login('setForm')">立即登录</div>
      </div>
    </el-card>
  </div>
</template>

<script>
import rules from "../untils/rule";
export default {
  name: "",
  data() {
    return {
      rules,
      setForm: {
        phone: "", //手机号
        password: "" //密码
      }
    };
  },
  methods: {
    register() {
      this.$router.push("/register");
    },
    login(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          this.$axios({
            method: "post",
            url: this.$store.state.domain + "/sld/user/login",
            data: this.setForm
          })
            .then(response => {
              if (response.data.code == 0) {
                //登录成功
                this.$message({
                  message: "恭喜你登录成功",
                  type: "success"
                });
                this.$router.push("/home"); //跳转
                var username = response.data.detail.username;
                sessionStorage.setItem("username", username);
              } else {
                this.$message.error(response.data.msg);
              }
            })
            .catch(function(error) {
              console.log(error);
            });
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.button {
  position: relative;
}
.forgetbtn {
  position: absolute;
  right: 0px;
  top: -30px;
}
.login {
  height: 100%;
  background-image: url("../../src/assets/city.jpg");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center center;
  background-size: cover;
}
h2 {
  position: absolute;
  font-family: "黑体";
  left: 2%;
  top: 3%;
  cursor: pointer;
  color: #fff;
}
p {
  color: #fff;
}
.but {
  background: rgba(0, 0, 0, 0.712);
  color: #fff;
  text-align: center;
  border-radius: 4px;
  cursor: pointer;
  padding: 10px;
  font-size: 16px;
  margin-top: 40px;
}
.but:hover {
  background: rgba(0, 0, 0, 0.747);
}
.insert {
  padding: 40px 28px 0px;
}
.box-card {
  position: relative;
  /* left: 33%; */
  margin: 0 auto;
  top: 18%;
  width: 520px;
  height: 350px;
  font-family: "黑体";
  font-size: 24px;
  padding: 20px 0 0;
}
.tit {
  width: 100%;
  text-align: center;
}
/* .login{
    background: rgb(246, 248, 248);
    width: 100%;
    height: 100%;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
} */
</style>
