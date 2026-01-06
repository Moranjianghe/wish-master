<script setup>
import { computed } from 'vue';

// 接收当前步骤作为prop
const props = defineProps({
  currentStep: {
    type: Number,
    required: true,
    validator: (value) => value >= 1 && value <= 3
  }
});

// 步骤文本：文案升级！更加“谜语人”和阴谋论风格
const steps = [
  { id: 1, text: '正在扫描灵魂签署痕迹...' }, // 原：正在审查... -> 现在的感觉：查你户口
  { id: 2, text: '正在检索因果律漏洞...' },   // 原：寻找漏洞... -> 现在的感觉：给你挖坑
  { id: 3, text: '正在生成不可逆的现实...' }   // 原：构建现实... -> 现在的感觉：你逃不掉了
];

// 计算当前激活的步骤
const activeStep = computed(() => {
  return props.currentStep;
});
</script>

<template>
  <div class="step-flow">
    <div class="steps-container">
      <div 
        v-for="step in steps" 
        :key="step.id"
        class="step"
        :class="{ 
          'active': step.id === activeStep,
          'completed': step.id < activeStep
        }"
      >
        <div class="step-indicator">
          <div class="step-circle">
            <span v-if="step.id < activeStep" class="step-check">✓</span>
            <span v-else class="step-number">{{ step.id }}</span>
          </div>
          <div class="step-line" v-if="step.id < steps.length"></div>
        </div>
        <div class="step-content">
          <p class="step-text">{{ step.text }}</p>
          <div v-if="step.id === activeStep" class="step-animation">
            <span class="dot"></span>
            <span class="dot"></span>
            <span class="dot"></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.step-flow {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
}

.steps-container {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.step {
  display: flex;
  align-items: flex-start;
}

.step-indicator {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-right: 16px;
}

.step-circle {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background-color: transparent; /* 变得更通透冷漠 */
  border: 2px solid #bdc3c7;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
  color: #bdc3c7;
  transition: all 0.5s ease;
  font-family: 'Courier New', monospace; /* 机打风格数字 */
}

/* 激活时：变成像是在警告的深红/紫色，或者保持高冷的黑色 */
.step.active .step-circle {
  background-color: #2c3e50;
  border-color: #2c3e50;
  color: white;
  box-shadow: 0 0 10px rgba(44, 62, 80, 0.3); /* 微微发光 */
}

/* 完成时：不再是安全的绿色，而是“契约已定”的紫色 */
.step.completed .step-circle {
  background-color: #8e44ad;
  border-color: #8e44ad;
  color: white;
}

.step-check {
  font-size: 14px;
}

.step-number {
  font-size: 14px;
}

.step-line {
  height: 24px;
  width: 2px;
  background-color: #eee;
  margin-top: 4px;
  transition: background-color 0.5s ease;
}

.step.completed .step-line {
  background-color: #8e44ad; /* 连线也变成紫色 */
}

.step-content {
  padding-top: 4px;
}

.step-text {
  margin: 0;
  font-size: 1rem;
  color: #95a5a6;
  transition: all 0.5s ease;
}

.step.active .step-text {
  color: #2c3e50;
  font-weight: 600;
  letter-spacing: 1px; /* 激活时字间距拉大，增加压迫感 */
}

.step.completed .step-text {
  color: #8e44ad;
  text-decoration: line-through; /* 完成后划掉，表示“命运已定，无法更改” */
  opacity: 0.7;
}

.step-animation {
  display: flex;
  gap: 4px;
  margin-top: 8px;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: #2c3e50;
  animation: pulse 1.4s infinite ease-in-out;
}

.dot:nth-child(2) { animation-delay: 0.2s; }
.dot:nth-child(3) { animation-delay: 0.4s; }

@keyframes pulse {
  0%, 100% { transform: scale(0.5); opacity: 0.3; }
  50% { transform: scale(1.2); opacity: 1; }
}

@media (max-width: 768px) {
  .step-text { font-size: 0.95rem; }
}
</style>