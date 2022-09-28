<template>

<!--  canvas画布-->
<canvas id="canvas" width="300" height="300"></canvas>


  <n-button type="info" style="display: inline-block;margin-left: 50px" @click="handdownload">下载</n-button>
</template>

<script setup>

import { ref, onMounted, onUnmounted } from "vue";


onMounted(() => {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");
  const img = new Image();
  img.src = "/src/assets/head.png";
  img.onload = () => {
    ctx.drawImage(img, 0, 0, 300, 300);
  };

//添加背景颜色

  ctx.fillStyle = "#fff";
  ctx.fillRect(0, 0, 300, 300);

let hongqi= new Image();
hongqi.src = "/src/assets/hongqi.png";
hongqi.onload = () => {
  ctx.drawImage(hongqi, 250, 249, 50, 50);  // 画图 0,0  300,300  画布的位置  300,300 画布的大小
};


});

//下载画布内容
const handdownload = () => {
  const canvas = document.getElementById("canvas");  //获取canvas
  const url = canvas.toDataURL("image/png");  //将canvas转换为图片
  const a = document.createElement("a");  //创建a标签
  document.body.appendChild(a);  //将a标签添加到body中
  a.href = url;
  a.download = "国庆小头像";
  a.click();
  document.body.removeChild(a);
};

</script>