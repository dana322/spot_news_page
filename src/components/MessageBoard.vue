<script setup>

const props = defineProps({
  imageSrc: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  source: {
    type: String,
    required: true,
  },
  time: {
    type: String,
    required: true,
  },
  videoTime: {
    type: String,
    required: true,
  }
});
</script>

<template>
  <div class="message-board">
    
    <div class="badge-wrapper">
        <img :src="imageSrc" alt="图片">
        <div class="badge-dot"></div>
        <div class="badge-number">{{ videoTime }}</div>     
    </div>
    <div class="info">
        <h3 class="title">{{ title }}</h3>
          <div class="wrapper">
            <p class="source">{{ source }}</p>
            <p class="dot">·</p>
            <p class="time">{{ time }}</p>
          </div>
    </div>
  </div>
</template>

<style scoped>

.message-board {
  margin: 10px 0;
}

.badge-wrapper {
  position: relative;
}

img {
  width: 100%;
  height: 80px;
  border-radius: 3px;
}

.badge-dot {
  position: absolute;
  top: -1px;
  right: 0px;
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background-color: #1989fa;
  border: 2px solid white;
}

.badge-number {
  position: absolute;
  bottom: 10px;
  right: 10px;
  font-size: 12px;
  color: white;
}

.title {
  font-size: 13px;
  margin: 2px 0;
  text-align: left;
}

.source {
  font-size: 12px;
  color: #888888;
  text-align: left;
}

.dot {
  margin: 0 2px;
}

.time, .dot {
  font-size: 12px;
  color: #888888;
}


.info .title {
  display: block;
}


.wrapper {
  display: flex;
  flex-direction: row;
}
.info .source,
.info .time {
  display: inline-block;
  margin: 2px 0;
}

</style>
