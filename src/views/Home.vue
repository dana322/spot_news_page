<template>
  <div class="home">
    <Header></Header>
     <MessageBoard
        v-for="(message, index) in messages"
        :key="index"
        :image-src="message.imageSrc"
        :title="message.title"
        :source="message.source"
        :time="message.time"
        :video-time="message.videoTime"
      />
  </div>
</template>

<script setup>
import MessageBoard from '../components/MessageBoard.vue';
import Header from '../components/Header.vue';
import { ref, onMounted } from 'vue';

import axios from 'axios';

// 定义响应数据变量
let data = [];
const messages = ref([]);

// 发起请求
const fetchData = async () => {
  const apiKey = 'b0e3a4b76d7deaa1f562f227a806d360';
  const num = 8;
  const apiUrl = `https://apis.tianapi.com/tiyu/index?key=${apiKey}&num=${num}`;

  try {
    const response = await axios.get(apiUrl);
    // 将响应数据保存到变量中
    data = response.data.result.newslist;
    messages.value = data.map(item => ({
      imageSrc: item.picUrl,
      title: item.title,
      source: item.source,
      time: calculateTime(item.ctime),
      videoTime: "109:09", 
    }));
  } catch (error) {
    console.error(error);
  }
};

const calculateTime = (ctime) => {
  const currentTime = new Date();
  const createTime = new Date(ctime);
  const diffTime = Math.floor((currentTime - createTime) / 1000); // 计算时间差，单位为秒

  if (diffTime < 60) {
    return `${diffTime}秒前`;
  } else if (diffTime < 3600) {
    const minutes = Math.floor(diffTime / 60);
    return `${minutes}分钟前`;
  } else if (diffTime < 86400) {
    const hours = Math.floor(diffTime / 3600);
    return `${hours}小时前`;
  } else {
    const days = Math.floor(diffTime / 86400);
    return `${days}天前`;
  }
};

onMounted(fetchData);




</script>

<style scoped>
.home {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  /* padding: 20px; */
}


.message-board {
  flex-basis: calc(50% - 10px);
}

</style>
