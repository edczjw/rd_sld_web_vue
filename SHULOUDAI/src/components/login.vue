<template>
  <div class="login">
    <h2>民盛赎楼贷信息平台</h2>
    <p class="phone">遇到问题 ?  可拨打客服电话：010-123456221</p>

    <el-card class="box-card">
    <div class="tit">登录</div>
        <div class="insert">
            <el-form :model="setForm" status-icon ref="setForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="输入手机号" prop="mobile" :rules="rules.phone">
                    <el-input v-model.trim="setForm.mobile" auto-complete="off"></el-input>
                </el-form-item>

                <el-form-item label="输入密码" prop="pass" :rules="rules.kong">
                    <el-input type="password" v-model.trim="setForm.pass"></el-input>
                </el-form-item>
            </el-form>
                <div class="but" @click="login('setForm')">立即登录</div>
        </div>
    </el-card>
  </div>
</template>

<script>
import rules from '../untils/rule'
export default {
  name: '',
  data () {
    return {
      rules,  
      setForm:{
          mobile:"",        //手机号
          pass:""           //密码
      }
    }
  },
  methods: {
      login(formName){
          this.$router.push("/home");//跳转
        //   this.$refs[formName].validate((valid) => {
        //   if (valid) {
        //             this.$axios({
        //                 method: 'post',
        //                 url: this.$store.state.domain +"/biz/user/register",
        //                 data: this.setForm,
        //             })
        //             .then(
        //                 response => {
        //                 if(response.data.code==0){
        //                     //注册成功
        //                     this.$message({
        //                         message: '恭喜你'+response.data.msg+'，欢迎进入登录。',
        //                         type: 'success'
        //                     });
                        
        //                 var username = response.data.detail.username;
        //                 sessionStorage.setItem("username", username);
                        

        //                 }else{
        //                     this.$message.error(response.data.msg);
        //                 }
        //                 }
        //             )
        //             .catch(function (error) {
        //                 console.log(error);
        //             });
        //       } else {
        //     console.log('error submit!!');
        //     return false;
        //   }
        // });
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2{
    position: absolute;
    font-family: '黑体';
    left: 2%;
    top: 3%;
    cursor: pointer;
}
.but{
    background: rgba(0, 0, 0, 0.712);
    color: #fff;
    text-align: center;
    border-radius: 4px;
    cursor: pointer;
    padding: 10px;
    font-size: 16px;
    margin-top: 40px;
}
.but:hover{
    background: rgba(0, 0, 0, 0.747);
}
.insert{
    padding: 40px 28px 0px;
}
.box-card{
    position: absolute;
    left: 35%;
    top: 18%;
    width: 520px;
    height: 350px;
    font-family: '黑体';
    font-size: 24px;
    padding: 20px 0 0;
}
.tit{
    width: 100%;
    text-align: center;

}
.login{
    background: rgb(246, 248, 248);
    width: 100%;
    height: 100%;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
