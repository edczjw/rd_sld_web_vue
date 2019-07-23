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
        <div v-if="this.action==1? true:false"  class="mess">
          <el-form :model="setForm" status-icon ref="setForm" class="demo-ruleForm">
                <el-form-item prop="name" :rules="rules.kong">
                  姓名
                    <el-input size="small" v-model.trim="setForm.name" auto-complete="off"></el-input>
                    <span><i class="el-icon-info"></i> 请确保您的姓名与身份证上的信息保持一致</span>
                </el-form-item>

                <el-form-item prop="phone" :rules="rules.phone">
                  电话
                    <el-input size="small" v-model.trim="setForm.phone"></el-input>
                    <span><i class="el-icon-info"></i> 请确保输入正确格式的手机号码</span>
                </el-form-item>

                <el-form-item prop="idcard" :rules="rules.checkid">
                  身份证号码
                    <el-input size="small" v-model.trim="setForm.idcard"></el-input>
                    <span><i class="el-icon-info"></i> 请确保您的身份证号码与身份证上的信息保持一致</span>
                </el-form-item>

                <el-form-item prop="bankid" :rules="rules.kong">
                  银行卡号
                    <el-input size="small" v-model.trim="setForm.bankid"></el-input>
                    <span><i class="el-icon-info"></i> 请确保输入正确格式的银行卡号</span>
                </el-form-item>
            </el-form>
                <div class="nextbut" @click="next('setForm')">下一步</div>
        </div>

        <!-- 影像资料 -->
        <div v-if="this.action==2? true:false" class="mess">
                <el-button size="mini" type="primary">身份证正面照</el-button>
                <el-row class="table-row">
                <el-col :span="4">
                  <el-upload
                    class="avatar-uploader"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                  </el-upload>
                </el-col>
                </el-row>

                <el-button size="mini" type="primary">身份证反面照</el-button>
                <el-row class="table-row">
                <el-col :span="4">
                  <el-upload
                    class="avatar-uploader"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                  </el-upload>
                </el-col>
                </el-row>

                <el-button size="mini" type="primary">业务办理照片</el-button>
                <el-row class="table-row">
                <el-col :span="4">
                  <el-upload
                    class="avatar-uploader"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                  </el-upload>
                </el-col>
                </el-row>
                <el-button size="mini" type="primary">借款合同</el-button>
                <el-row class="table-row">
                <el-col :span="4">
                  <el-upload
                    class="avatar-uploader"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                  </el-upload>
                </el-col>
                </el-row>
                <el-button size="mini" type="primary">委托合同</el-button>
                <el-row class="table-row">
                <el-col :span="4">
                  <el-upload
                    class="avatar-uploader"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                  </el-upload>
                </el-col>
                </el-row>
                <el-button size="mini" type="primary">质押合同</el-button>
                <el-row class="table-row">
                <el-col :span="4">
                  <el-upload
                    class="avatar-uploader"
                    action="https://jsonplaceholder.typicode.com/posts/"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                  </el-upload>
                </el-col>
                </el-row>
                <div class="nextbut" @click="next2()">下一步</div>
        </div>

        <!-- 预览 -->
        <div v-if="this.action==3? true:false" class="mess">
                <el-row class="messrow">
                  <el-col :span="6">
                    姓名
                  </el-col>
                  <el-col :span="18">
                    {{setForm.name}}
                  </el-col>
                </el-row>
                <el-row class="messrow">
                  <el-col  :span="6">
                    电话号码
                  </el-col>
                  <el-col  :span="18">
                    {{setForm.phone}}
                  </el-col>
                </el-row>
                <el-row class="messrow">
                  <el-col  :span="6">
                    身份证号码
                  </el-col>
                  <el-col  :span="18">
                    {{setForm.idcard}}
                  </el-col>
                </el-row>
                <el-row class="messrow">
                  <el-col  :span="6">
                    银行卡号
                  </el-col>
                  <el-col  :span="18">
                    {{setForm.bankid}}
                  </el-col>
                </el-row>

                <el-row class="imgrow">
                  <el-col  :span="6">
                    身份证正面照
                  </el-col>
                  <el-col  :span="18">
                    <img src="../assets/city.jpg" alt="">
                  </el-col>
                </el-row>

                <el-row class="imgrow">
                  <el-col  :span="6">
                    身份证反面照
                  </el-col>
                  <el-col  :span="18">
                    <img src="../assets/city.jpg" alt="">
                  </el-col>
                </el-row>

                <el-row class="imgrow">
                  <el-col  :span="6">
                    业务办理照片
                  </el-col>
                  <el-col  :span="18">
                    <img src="../assets/city.jpg" alt="">
                  </el-col>
                </el-row>

                <el-row class="imgrow">
                  <el-col  :span="6">
                    借款合同
                  </el-col>
                  <el-col  :span="18">
                    <img src="../assets/city.jpg" alt="">
                  </el-col>
                </el-row>

                <el-row class="imgrow">
                  <el-col  :span="6">
                    委托合同
                  </el-col>
                  <el-col  :span="18">
                    <img src="../assets/city.jpg" alt="">
                  </el-col>
                </el-row>

                <el-row class="imgrow">
                  <el-col  :span="6">
                    质押合同
                  </el-col>
                  <el-col  :span="18">
                    <img src="../assets/city.jpg" alt="">
                  </el-col>
                </el-row>

                <div class="nextbut" @click="next2()">提交</div>
        </div>

      </el-card>
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
      action:'3',
      username: '小米',
       imageUrl: '',
      setForm:{
        name:"",
        phone:"",
        idcard:"",
        bankid:""
      }
    }
  },
  methods: {
    next2(){
      if(this.action=='2'){
        this.action='3';
      }else if(this.action=='3'){
        this.$alert('成功!', '提交信息', {
          confirmButtonText: '确定',
          center: true,
          type: 'success',
          callback: action => {
            this.action='1';
          }
        });
        
      }
    },
    handleAvatarSuccess(res, file) {
        this.imageUrl = URL.createObjectURL(file.raw);
      },
      beforeAvatarUpload(file) {
        const isJPG = file.type === 'image/jpeg';
        const isLt2M = file.size / 1024 / 1024 < 2;

        if (!isJPG) {
          this.$message.error('上传头像图片只能是 JPG 格式!');
        }
        if (!isLt2M) {
          this.$message.error('上传头像图片大小不能超过 2MB!');
        }
        return isJPG && isLt2M;
      },
    next(formName){
      this.$refs[formName].validate((valid) => {
          if (valid) {
              if(this.action=='1'){
                this.action='2';
              }else if(this.action=='2'){
                this.action='3';
              }
             } else {
            console.log('error submit!!');
            return false;
          }
        });

    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.mess{
  padding: 20px 70px;
  span{
    font-size: 12px;
  }
  .nextbut{
    width:60%;
    padding: 10px;
    text-align: center;
    margin: 0 auto;
    background: rgb(175, 48, 48);
    color: #fff;
    cursor: pointer;
  }
  .nextbut:hover{
    background: rgb(204, 39, 39);
  }
  .imgrow{
      text-align: center;
      border: 1px solid #ccc;
      border-bottom: none;
      border-right: none;
      margin-top: 20px;
      margin-bottom: 20px;
      .el-col{
        cursor: pointer;
        border-bottom: 1px solid #ccc;
        border-right: 1px solid #ccc;
        height: 240px;
        line-height: 240px;
        
        img{
          width: 360px;
          height: 240px;
        }
      }
  }
  .messrow{
      text-align: center;
      border: 1px solid #ccc;
      border-bottom: none;
      border-right: none;
      margin-top: 10px;
      &:last-child {
        margin-bottom: 0;
        border-bottom: none;
      }
    .el-col{
      cursor: pointer;
      border-bottom: 1px solid #ccc;
      border-right: 1px solid #ccc;
      height: 40px;
      line-height: 40px;
    }
    .el-col:hover{
      background: #ccc;
    }
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
  z-index: 999;
  line-height: 50px;
  background: #fff;
  position: absolute;
  top: 30px;
  padding: 0 18%;
  border-bottom: 1px solid #eee;
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
  z-index: 999;
  height: 30px;
  line-height: 30px;
  background: rgb(26, 24, 24);
  position: absolute;
  top: 0;
  padding: 0 20px;
  p{
    color: #fff;
    position: absolute;
    right: 18%;
    font-size: 14px;
  }
}
.card{
  width: 65%;
  margin: 0 auto;
  height: 100%;
  margin-top: 10px;
  padding: 0 0 45px;
  .card1{
    width: 18%;
    height: 95%;
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
    height: 100%;
    overflow-y: scroll;
  }
}
.index{
  background-image: url('../assets/city.jpg');
  background-repeat: no-repeat;
  background-attachment: scroll;
  background-position: center center;
  background-size: cover;
    width: 100%;
    height: 100%;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    padding: 80px 0 0;
}

</style>
