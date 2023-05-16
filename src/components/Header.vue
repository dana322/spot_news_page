<template>
  <header class="header">
    <div class="search-box">
      <input type="text" placeholder="搜索频道">
    </div>
    <div class="icons">
      <img src="../assets/read.svg" alt="">
      <div class="live-wrapper">
        <img src="../assets/live.svg" alt="">
        <span class="notification">1</span>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 5px;
}

.search-box {
  position: relative;
}

.search-box input[type="text"] {
  padding: 5px 10px 5px 20px; /* 调整内边距，使图标留出空间 */
  border: none;
  outline: none;
  background-image: url('../assets/search.svg');
  background-repeat: no-repeat;
  background-position: 3px center;
  background-size: 16px;
  background-color: #cccccc46;
  width: 60px;
  border-radius: 27px;
}

.icons {
  display: flex;
}

img {
  width: 20px;
  margin-left: 20px;
}
.notification {
  position: absolute;
  top: -8px;
  right: -8px;
  background-color: red;
  color: white;
  border-radius: 50%;
  width: 16px;
  height: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 10px;
}
.live-wrapper {
  position: relative;
}
</style>

