<template>
  <div class="index">
    <div class="top-banner">
    <p>Hi~{{this.username}}</p>
    </div>
    <div class="mo">
      <p>民盛赎楼贷信息平台</p>
    </div>

    <div class="card">
      <el-card class="card1">
        <div class="step">
         <el-steps :active="this.action" direction="vertical">
          <el-step title="基本信息" icon="el-icon-edit"></el-step>
          <el-step title="影像资料" icon="el-icon-upload"></el-step>
          <el-step title="预览" icon="el-icon-picture"></el-step>
        </el-steps>
        </div>
      </el-card>
      <el-card class="card2">
        <div class="cute-tip">
          <p v-if="this.action==1? true:false">基本信息</p>
          <p v-if="this.action==2? true:false">影像资料</p>
          <p v-if="this.action==3? true:false">预览</p>
        </div>
        <!-- 基本信息 -->
        <div class="mess">
          <el-form :model="setForm" status-icon ref="setForm" class="demo-ruleForm">
                <el-form-item prop="mobile" :rules="rules.kong">
                  姓名
                    <el-input size="small" v-model.trim="setForm.mobile" auto-complete="off"></el-input>
                    <span>请确保您的姓名与身份证上的信息保持一致</span>
                </el-form-item>

                <el-form-item prop="pass" :rules="rules.phone">
                  电话
                    <el-input size="small" type="password" v-model.trim="setForm.pass"></el-input>
                </el-form-item>

                <el-form-item prop="pass" :rules="rules.checkid">
                  身份证号码
                    <el-input size="small" type="password" v-model.trim="setForm.pass"></el-input>
                </el-form-item>

                <el-form-item prop="pass" :rules="rules.kong">
                  银行卡号
                    <el-input size="small" type="password" v-model.trim="setForm.pass"></el-input>
                </el-form-item>
            </el-form>
                <div class="but" @click="login('setForm')">下一步</div>
        </div>

      </el-card>
    </div>

    <div class="bottom">
      <p>© 版权所有。民盛互联网小额贷款有限公司。 不得转载。</p>
    </div>
  </div>
</template>

<script>
import rules from '../untils/rule'
export default {
  name: '',
  data () {
    return {
      rules,  
      action:'1',
      username: '小米',
      setForm:{
        mobile:"",
        pass:""
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.mess{
  padding: 50px;
  .span{
    font-size: 12px;
  }
}
.cute-tip{
  width: 100%;
  padding-left: 10px;
  height: 28px;
  line-height: 28px;
  border-left: 3px solid rgb(143, 92, 92);
  background: #eee;
  
}
.mo{
  width: 100%;
  height: 50px;
  line-height: 50px;
  background: #fff;
  position: absolute;
  top: 30px;
  padding: 0 20%;
  p{
    font-size: 28px;
    line-height: 50px;
    font-weight: bolder;
    font-family: 'Times New Roman', Times, serif;
    padding: 0 20px 0 0;
  }
}
.top-banner{
  width: 100%;
  height: 30px;
  line-height: 30px;
  background: rgb(26, 24, 24);
  position: absolute;
  top: 0;
  padding: 0 20px;
  p{
    color: #fff;
    position: absolute;
    right: 20%;
    font-size: 14px;
  }
}
.card{
  width: 60%;
  margin: 0 auto;
  height: 100%;
  margin-top: 15px;
  .card1{
    width: 18%;
    height: 97%;
    float: left;
    position: relative;
    text-align: center;
    .step{
      position: absolute;
      height: 80%;
      width: 80%;
      text-align: center;
      .el-step__title {
        font-size: 12px !important;
      }
    }
  }
  .card2{
    width: 81%;
    float: right;
    height: 97%;
  }
}
.index{
    width: 100%;
    height: 100%;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    padding: 80px 0 0;
}
.bottom{
  position: relative;
  width: 100%;
  bottom: 0;
  background: rgb(26, 24, 24);
  height: 50px;
  line-height:50px;
  text-align: center;
  color: #fff;
}
</style>
