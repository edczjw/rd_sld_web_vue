<template>
  <div id="app">
    <router-view/>
    <div class="bottom">
      <p>© 版权所有。民盛互联网小额贷款有限公司。 不得转载。</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

/* 整体布局样式 */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: '黑体';

  text-decoration: none;
}

html {
  height: 100%;
}

body {
  height: 100%;
  overflow: hidden;
}
#app {
  height: 100%;
  overflow: hidden;
}

.bottom{
  position: fixed;
  width: 100%;
  z-index: 999;
  bottom: 0;
  background: rgb(26, 24, 24);
  height: 30px;
  line-height:30px;
  text-align: center;
  color: #fff;
}
.phone{
    position: absolute;
    font-family: '苹方';
    right: 2%;
    top: 2%;
    font-weight: bold;
    font-size: 12px;
    cursor: pointer;
    color: rgb(62, 72, 160);
}
.table-row{
  margin: 20px 20px 20px 0;
}
.avatar-uploader .el-upload {
    border: 1px dashed #d9d9d9;
    border-radius: 6px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .avatar-uploader .el-upload:hover {
    border-color: #409EFF;
  }
  .avatar-uploader-icon {
    font-size: 28px;
    color: #8c939d;
    width: 368px;
    height: 178px;
    line-height: 178px;
    text-align: center;
  }
  .avatar {
    width: 368px;
    height: 178px;
    display: block;
  }
</style>
