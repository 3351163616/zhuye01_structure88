<template>
  <div id="loading-box" :class="store.imgLoadStatus ? 'loaded' : ''">
    <div class="loading-left-bg"></div>
    <div class="loading-right-bg"></div>
    <div class="spinner-box">
      <div class="loader">
        <div class="inner one"></div>
        <div class="inner two"></div>
        <div class="inner three"></div>
      </div>
      <div class="loading-word">
        <p class="loading-title">{{ siteName }}</p>
        <p>作者：杨潇</p>
        <p>加载中ing...</p>
        <p>🙌🙌建议使用电脑打开哦🙌🙌</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { mainStore } from "@/store";

const store = mainStore();

// 配置
const siteName = import.meta.env.VITE_SITE_NAME;
</script>

<style lang="scss" scoped>
#loading-box .loading-left-bg,
#loading-box .loading-right-bg {
  position: fixed;
  z-index: 999998;
  width: 50%;
  height: 100%;
  background-color: rgb(81 81 81 / 80%);
  transition: all 0.4s cubic-bezier(0.42, 0, 0, 1.01);
  /* 调整过渡效果 */
  backdrop-filter: blur(10px);
}

#loading-box .loading-right-bg {
  right: 0;
}

#loading-box>.spinner-box {
  position: fixed;
  z-index: 999999;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
}

#loading-box .spinner-box .loading-word {
  position: absolute;
  color: #ffffff;
  font-size: 0.95rem;
  transform: translateY(64px);
  text-align: center;
}

p.loading-title {
  font-size: 1.25rem;
  margin: 20px 10px 4px 10px;
}

#loading-box .spinner-box .configure-core {
  width: 100%;
  height: 100%;
  background-color: #37474f;
}

div.loaded div.loading-left-bg {
  transform: translate(-100%, 0);
}

div.loaded div.loading-right-bg {
  transform: translate(100%, 0);
}

div.loaded div.spinner-box {
  display: none !important;
}

.loader {
  position: absolute;
  top: calc(50% - 32px);
  left: calc(50% - 32px);
  width: 64px;
  height: 64px;
  border-radius: 50%;
  perspective: 800px;
  transition: all 0.3s cubic-bezier(0.42, 0, 0, 1.01);
  /* 调整过渡效果 */
}

.inner {
  position: absolute;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

.inner.one {
  left: 0%;
  top: 0%;
  animation: rotate-one 0.5s linear infinite;
  /* 调整旋转动画 */
  border-bottom: 3px solid #EFEFFA;
}

.inner.two {
  right: 0%;
  top: 0%;
  animation: rotate-two 0.5s linear infinite;
  /* 调整旋转动画 */
  border-right: 3px solid #EFEFFA;
}

.inner.three {
  right: 0%;
  bottom: 0%;
  animation: rotate-three 0.5s linear infinite;
  /* 调整旋转动画 */
  border-top: 3px solid #EFEFFA;
}

@keyframes rotate-one {
  0% {
    transform: rotateX(35deg) rotateY(-45deg) rotateZ(0deg);
  }

  100% {
    transform: rotateX(35deg) rotateY(-45deg) rotateZ(360deg);
  }
}

@keyframes rotate-two {
  0% {
    transform: rotateX(50deg) rotateY(10deg) rotateZ(0deg);
  }

  100% {
    transform: rotateX(50deg) rotateY(10deg) rotateZ(360deg);
  }
}

@keyframes rotate-three {
  0% {
    transform: rotateX(35deg) rotateY(55deg) rotateZ(0deg);
  }

  100% {
    transform: rotateX(35deg) rotateY(55deg) rotateZ(360deg);
  }
}
</style>
