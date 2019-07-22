<template>
  <div id="app">
    <router-view/>
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
  background-image: url('../src/assets/city.jpg');
  background-repeat: no-repeat;
  background-attachment: scroll;
  background-position: center center;
  background-size: cover;
  height: 100%;
  overflow-y: scroll;
}
#app {
  height: 100%;
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
</style>
