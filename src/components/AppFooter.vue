<script setup>
// AppFooter.vue - 页面底部组件
</script>

<template>
  <footer class="app-footer">
    <div class="divider"></div>
    
    <div class="system-log">
      <span class="log-tag">[ System Patch v1.1 ]</span>
      <p>
        贪婪阈值已解除锁定，许愿字数扩充至 80。
        <span class="creepy-note">
          （注：允许你编织更复杂的欲望罗网，但请记住...网越大，作为猎物的你就越难逃脱。）
        </span>
      </p>
    </div>

    <div class="disclaimer">
      所有的愿望都已在暗中标好了代价。本系统基于逻辑推演，不承担任何因果责任。<br>
      智慧来源：DeepSeek-V3 
    </div>
    <div class="copyright">
      © 2026 完美许愿器 | 
      <a href="https://github.com/senzi/wish-master" target="_blank">
        GitHub Source
      </a>
      | 
      <a href="https://weibo.com/u/7402396589" target="_blank">
        @阿尼亚是安妮亞
      </a>
    </div>
    <div class="warning-text">CAVEAT EMPTOR</div>
  </footer>
</template>

<style scoped>
.app-footer {
  margin-top: auto;
  padding: 2rem 0;
  background-color: transparent;
  color: #7f8c8d;
  font-size: 12px;
  text-align: center;
  width: 100%;
}

.divider {
  height: 1px;
  border-top: 1px dashed #ddd;
  margin-bottom: 1.5rem;
  width: 100%;
}

/* 新增样式的阴暗部分 */
.system-log {
  margin-bottom: 1.5rem;
  font-family: 'Courier New', Courier, monospace; /* 打字机字体增加机密感 */
  font-size: 11px;
  color: #95a5a6;
  background-color: rgba(0, 0, 0, 0.02);
  padding: 10px;
  border-radius: 4px;
  display: inline-block;
  max-width: 95%;
}

.log-tag {
  color: #c0392b; /* 暗红色，像警告 */
  font-weight: bold;
  display: block;
  margin-bottom: 4px;
  letter-spacing: 1px;
}

.creepy-note {
  display: block;
  margin-top: 4px;
  font-size: 10px;
  color: #bdc3c7;
  font-style: italic;
  transform: scale(0.95); /* 稍微缩小，像是在窃窃私语 */
  transition: all 0.5s ease;
}

/* 鼠标悬停时，阴谋显露 */
.system-log:hover .creepy-note {
  color: #8e44ad; /* 变成诡异的紫色 */
  text-shadow: 0 0 5px rgba(142, 68, 173, 0.3);
}

.disclaimer {
  margin-bottom: 0.8rem;
  line-height: 1.8;
  font-style: italic;
}

.copyright {
  line-height: 1.5;
  letter-spacing: 1px;
}

.copyright a {
  color: #2c3e50;
  text-decoration: none;
  border-bottom: 1px solid #bdc3c7;
  transition: all 0.3s ease;
}

.copyright a:hover {
  color: #8e44ad;
  border-bottom-color: #8e44ad;
}

.warning-text {
  margin-top: 1rem;
  font-size: 10px;
  letter-spacing: 4px;
  color: #bdc3c7;
  font-weight: bold;
}

@media (max-width: 768px) {
  .app-footer {
    padding: 1.5rem 10px;
  }
}
</style>