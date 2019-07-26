<template>
  <div class="index">
    <div class="top-banner">
      <p style="cursor:pointer;">
        <i class="el-icon-location-outline"></i>
        Hi~{{this.username}}
      </p>
      <span @click="goBack" title="安全退出" style="cursor:pointer;">
        <i class="el-icon-remove-outline"></i> 退出
      </span>
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
        <div v-if="this.action==1? true:false" class="mess">
          <el-form :model="setForm" status-icon ref="setForm" class="demo-ruleForm">
            <el-form-item prop="name" :rules="rules.kong">
              姓名
              <el-input size="small" v-model.trim="setForm.name" auto-complete="off"></el-input>
              <span>
                <i class="el-icon-info"></i> 请确保您的姓名与身份证上的信息保持一致
              </span>
            </el-form-item>

            <el-form-item prop="phone" :rules="rules.phone">
              电话
              <el-input size="small" v-model.trim="setForm.phone"></el-input>
              <span>
                <i class="el-icon-info"></i> 请确保输入正确格式的手机号码
              </span>
            </el-form-item>

            <el-form-item prop="idcard" :rules="rules.checkid">
              身份证号码
              <el-input size="small" v-model.trim="setForm.idcard"></el-input>
              <span>
                <i class="el-icon-info"></i> 请确保您的身份证号码与身份证上的信息保持一致
              </span>
            </el-form-item>

            <el-form-item prop="bankid" :rules="rules.kong">
              银行卡号
              <el-input size="small" v-model.trim="setForm.bankid"></el-input>
              <span>
                <i class="el-icon-info"></i> 请确保输入正确格式的银行卡号
              </span>
            </el-form-item>
          </el-form>
          <div class="nextbut" @click="next('setForm')">下一步</div>
        </div>

        <!-- 影像资料 -->
        <div v-if="this.action==2? true:false" class="mess">
          <el-button size="mini" type="primary">身份证正面照</el-button>
          <el-row class="table-row">
            <el-col :span="4">
              <!-- <el-upload
                class="avatar-uploader"
                action
                drag
                :on-success="handleAvatarSuccess"
                :before-upload="beforeAvatarUpload"
                :limit="1"
                :http-request="Upload1"
                :file-list="fileList1"
                :on-exceed="handleExceed1"
                :on-change="handleChange1"
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
              </el-upload>-->
              <el-upload
                class="avatar-uploader"
                drag
                :limit="12"
                :http-request="Upload6"
                :file-list="fileList6"
                :on-exceed="handleExceed6"
                :before-upload="beforeAvatarUpload6"
                :on-change="handleChange6"
                multiple
                action
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
              </el-upload>
              <el-progress
                v-if="videoFlag6"
                :percentage="videoUploadPercent6"
                style="margin-top:30px;"
              ></el-progress>
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
                :before-upload="beforeAvatarUpload"
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
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
                :before-upload="beforeAvatarUpload"
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
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
                :before-upload="beforeAvatarUpload"
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
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
                :before-upload="beforeAvatarUpload"
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
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
                :before-upload="beforeAvatarUpload"
              >
                <img v-if="imageUrl" :src="imageUrl" class="avatar" />
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
              </el-upload>
            </el-col>
          </el-row>
          <div class="nextbut" @click="next2()">下一步</div>
        </div>

        <!-- 预览 -->
        <div v-if="this.action==3? true:false" class="mess">
          <el-row class="messrow">
            <el-col :span="6">姓名</el-col>
            <el-col :span="18">{{setForm.name}}</el-col>
          </el-row>
          <el-row class="messrow">
            <el-col :span="6">电话号码</el-col>
            <el-col :span="18">{{setForm.phone}}</el-col>
          </el-row>
          <el-row class="messrow">
            <el-col :span="6">身份证号码</el-col>
            <el-col :span="18">{{setForm.idcard}}</el-col>
          </el-row>
          <el-row class="messrow">
            <el-col :span="6">银行卡号</el-col>
            <el-col :span="18">{{setForm.bankid}}</el-col>
          </el-row>

          <el-row class="imgrow">
            <el-col :span="6">身份证正面照</el-col>
            <el-col :span="18">
              <img src="../assets/city.jpg" alt />
            </el-col>
          </el-row>

          <el-row class="imgrow">
            <el-col :span="6">身份证反面照</el-col>
            <el-col :span="18">
              <img src="../assets/city.jpg" alt />
            </el-col>
          </el-row>

          <el-row class="imgrow">
            <el-col :span="6">业务办理照片</el-col>
            <el-col :span="18">
              <img src="../assets/city.jpg" alt />
            </el-col>
          </el-row>

          <el-row class="imgrow">
            <el-col :span="6">借款合同</el-col>
            <el-col :span="18">
              <img src="../assets/city.jpg" alt />
            </el-col>
          </el-row>

          <el-row class="imgrow">
            <el-col :span="6">委托合同</el-col>
            <el-col :span="18">
              <img src="../assets/city.jpg" alt />
            </el-col>
          </el-row>

          <el-row class="imgrow">
            <el-col :span="6">质押合同</el-col>
            <el-col :span="18">
              <img src="../assets/city.jpg" alt />
            </el-col>
          </el-row>

          <div class="nextbut" @click="next2()">提交</div>
        </div>
      </el-card>
    </div>
  </div>
</template>

<script>
import rules from "../untils/rule";
export default {
  name: "",
  data() {
    return {
      rules,
      fileList1: [], //文件容器
      videoFlag1: false, //进度条
      idcardFront: "", //
      videoUploadPercent1: 0,
      action: 2,
      username: "小米",
      imageUrl: "",
      setForm: {
        name: "",
        phone: "",
        idcard: "",
        bankid: "",
        idcardFront: ""
      }
    };
  },
  methods: {
    //上传身份证正面
    Upload6(file) {
      var _that = this;
      this.videoFlag1 = true;
      const OSS = require("ali-oss");
      let _self = this;
      var bucket; //OSS文件名称
      var region;
      var extranet;
      var accessKeyId;
      var accessKeySecret;
      this.$axios({
        method: "post",
        url: this.$store.state.domain + "/sld/getAliyunOss"
      }).then(
        response => {
          // 向后台发请求 拉取OSS相关配置

          //后端提供数据
          const client = new OSS({
            region: "oss-cn-shenzhen", // 服务器集群地区
            extranet: response.data.extranet,
            accessKeyId: response.data.secretId, // OSS帐号
            accessKeySecret: response.data.secretKey, // OSS 密码
            bucket: response.data.bucket // 阿里云上存储的 Bucket
          });

          // 存储路径，并且给图片改成唯一名字
          var fileName = file.file.name;

          this.receivables.push(fileName);

          //后缀名
          const suffix = fileName.substr(fileName.indexOf("."));

          //时间戳
          const obj = this.timestamp();

          //时间戳
          const obj2 = this.timestamp1();

          //获取企业编号
          // const enterpriseNo = sessionStorage.getItem("enterpriseNo");

          const storeAs =
            "test/sld/userinfo/" +
            obj +
            "/cooperative/" +
            obj2 +
            "-" +
            fileName;

          this.setForm.receivables.push(
            "http://slloan.oss-cn-shenzhen.aliyuncs.com/" + storeAs
          );

          //上传
          client
            .multipartUpload(storeAs, file.file, {
              progress: function(p) {
                //获取进度条的值
                // console.log(p)
                _that.videoUploadPercent1 = p * 100;
              }
            })
            .then(res => {
              if (res.url != null || res.url != "") {
                // console.log('服务器返回的文件url：')

                //返回服务器文件url
                // console.log(res.url)
                this.videoFlag1 = false;
                _that.videoUploadPercent1= 0;
                this.$notify({
                  title: "上传结果",
                  type: "success",
                  offset: 100,
                  dangerouslyUseHTMLString: true,
                  message:
                    "<strong>" + file.file.name + "文件上传成功！</strong>",
                  position: "bottom-left"
                });
              }
            })
            .catch(err => {
              this.$message.error("上传文件异常:" + err);
              console.log("上传文件异常：");
              console.log(err);
            });
          //失败
        },
        //打印
        response => {
          console.log(response);
        }
      );
    },
    handleExceed1(files, fileList) {
      this.$message.warning(
        `当前限制选择 1 个文件，本次选择了 ${
          files.length
        } 个文件，共选择了 ${files.length + fileList.length} 个文件`
      );
    },
    beforeAvatarUpload1(file) {
      const length = this.fileList1.length <= 2;
      const isJPG = file.type === "image/jpeg";
      const isLt2M = file.size / 1024 / 1024 < 2;
      if (!length) {
        this.$message.error("此项上传文件数量不得大于1份，上传第2份文件失败！");
      }
      if (!isJPG) {
        this.$message.error("上传头像图片只能是 JPG 格式!");
      }
      if (!isLt2M) {
        this.$message.error("上传头像图片大小不能超过 2MB!");
      }
      return length && isLt20M && isJPG;
    },
    //对文件列表进行控制
    handleChange1(file, fileList) {
      this.fileList1 = fileList.slice(-3);
    },
    //  时间戳
    timestamp() {
      const time = new Date();
      const y = time.getFullYear();
      const m = time.getMonth() + 1;
      const d = time.getDate();
      const h = time.getHours();
      const mm = time.getMinutes();
      const s = time.getSeconds();
      return "" + y + "-" + this.Add0(m) + "-" + this.Add0(d);
    },
    Add0: function(m) {
      return m < 10 ? "0" + m : m;
    },

    //  时间戳1
    timestamp1() {
      const time = new Date();
      const y = time.getFullYear();
      const m = time.getMonth() + 1;
      const d = time.getDate();
      const h = time.getHours();
      const mm = time.getMinutes();
      const s = time.getSeconds();
      return (
        "" +
        y +
        "-" +
        this.Add1(m) +
        "-" +
        this.Add1(d) +
        "_" +
        this.Add1(h) +
        this.Add1(mm) +
        this.Add1(s)
      );
    },
    Add1: function(m) {
      return m < 10 ? "0" + m : m;
    },
    next2() {
      if (this.action == "2") {
        this.action = "3";
      } else if (this.action == "3") {
        this.$alert("成功!", "提交信息", {
          confirmButtonText: "确定",
          center: true,
          type: "success",
          callback: action => {
            this.action = "1";
          }
        });
      }
    },
    //退出登陆
    goBack() {
      this.$confirm("确认退出吗?", "提示", {})
        .then(() => {
          this.$router.push("/login");
        })
        .catch(() => {});
    },
    handleAvatarSuccess(res, file) {
      this.imageUrl = URL.createObjectURL(file.raw);
    },
    beforeAvatarUpload(file) {
      const isJPG = file.type === "image/jpeg";
      const isLt2M = file.size / 1024 / 1024 < 2;

      if (!isJPG) {
        this.$message.error("上传头像图片只能是 JPG 格式!");
      }
      if (!isLt2M) {
        this.$message.error("上传头像图片大小不能超过 2MB!");
      }
      return isJPG && isLt2M;
    },
    next(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          if (this.action == "1") {
            this.action = "2";
          } else if (this.action == "2") {
            this.action = "3";
          }
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
<style lang="less" scoped>
.mess {
  padding: 20px 70px;
  span {
    font-size: 12px;
  }
  .nextbut {
    width: 60%;
    padding: 10px;
    text-align: center;
    margin: 0 auto;
    background: rgb(175, 48, 48);
    color: #fff;
    cursor: pointer;
  }
  .nextbut:hover {
    background: rgb(204, 39, 39);
  }
  .imgrow {
    text-align: center;
    border: 1px solid #ccc;
    border-bottom: none;
    border-right: none;
    margin-top: 20px;
    margin-bottom: 20px;
    .el-col {
      cursor: pointer;
      border-bottom: 1px solid #ccc;
      border-right: 1px solid #ccc;
      height: 240px;
      line-height: 240px;

      img {
        width: 360px;
        height: 240px;
      }
    }
    .el-col:hover {
      background: rgb(230, 228, 228);
    }
  }
  .messrow {
    text-align: center;
    border-top: 1px solid #ccc;
    border-left: 1px solid #ccc;
    border-bottom: none;
    border-right: none;
    // margin-top: 10px;
    .el-col {
      cursor: pointer;
      border-bottom: 1px solid #ccc;
      border-right: 1px solid #ccc;
      height: 40px;
      line-height: 40px;
    }
    .el-col:hover {
      background: rgb(230, 228, 228);
    }
  }
}
.cute-tip {
  width: 100%;
  padding-left: 10px;
  height: 38px;
  line-height: 38px;
  border-left: 4px solid rgb(143, 92, 92);
  background: #eee;
  font-weight: bolder;
}
.mo {
  width: 100%;
  height: 50px;
  z-index: 999;
  line-height: 50px;
  background: #fff;
  position: absolute;
  top: 30px;
  padding: 0 18%;
  border-bottom: 1px solid #eee;
  p {
    font-size: 32px;
    line-height: 50px;
    font-weight: bolder;
    font-family: "Times New Roman", Times, serif;
    padding: 0 20px 0 0;
  }
}
.top-banner {
  width: 100%;
  z-index: 999;
  height: 30px;
  line-height: 30px;
  background: rgb(26, 24, 24);
  position: absolute;
  top: 0;
  padding: 0 20px;
  p {
    color: #fff;
    position: absolute;
    right: 18%;
    font-size: 14px;
  }
  p:hover {
    color: rgb(143, 110, 110);
  }
  span {
    color: #fff;
    font-size: 14px;
    position: absolute;
    left: 18%;
  }
  span:hover {
    color: rgb(143, 110, 110);
  }
}
.card {
  width: 65%;
  margin: 0 auto;
  margin-top: 10px;
  padding: 0 0 45px;
  .card1 {
    width: 16%;
    height: 100%;
    float: left;
    text-align: center;
    .step {
      height: 600px;
      width: 80%;
      text-align: center;
      .el-step__title {
        font-size: 12px !important;
      }
    }
  }
  .card2 {
    width: 83%;
    float: right;
    height: 100%;
    margin-bottom: 100px;
  }
}
.index {
  width: 100%;
  height: 100%;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  padding: 80px 0 0;
}
</style>
