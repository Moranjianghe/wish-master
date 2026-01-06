<script setup>
// App.vue - 主应用组件
</script>

<template>
  <div class="app">
    <div class="app-background"></div>
    <div class="content-wrapper">
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </div>
  </div>
</template>

<style>
/* 全局样式 */
:root {
  --primary-color: #2c3e50;
  --accent-color: #8e44ad;
  --bg-color: #f8f9fa;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* 自定义滚动条 - 让系统感更强 */
::-webkit-scrollbar {
  width: 6px;
}
::-webkit-scrollbar-track {
  background: transparent;
}
::-webkit-scrollbar-thumb {
  background: #bdc3c7;
  border-radius: 3px;
}
::-webkit-scrollbar-thumb:hover {
  background: var(--primary-color);
}

/* 选中文字变成“魔女紫” */
::selection {
  background-color: rgba(142, 68, 173, 0.2);
  color: var(--accent-color);
}

body {
  font-family: 'PingFang SC', 'Helvetica Neue', Helvetica, 'Microsoft YaHei', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--primary-color);
  background-color: var(--bg-color);
  line-height: 1.6;
  overflow-x: hidden; /* 防止因为动画出现横向滚动条 */
}

.app {
  min-height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
}

/* 背景特效层：制造一种“聚焦”或“幽闭”的潜意识感觉 */
.app-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: radial-gradient(circle at 50% 50%, #ffffff 0%, #ecf0f1 100%);
  /* 可以在这里加噪点图片增加胶片感，如果需要的话 */
  pointer-events: none;
}

.content-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  position: relative;
  z-index: 1;
}

button {
  cursor: pointer;
  font-family: inherit;
}

input, textarea {
  font-family: inherit;
}

/* 页面切换动画：更幽灵般的淡入淡出 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.fade-enter-from {
  opacity: 0;
  transform: translateY(10px); /* 新页面从下方隐约浮现 */
}

.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px); /* 旧页面向上消散 */
}
</style>