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
  height: 100%;
}

#app {
  height: 100%;
}

</style>
