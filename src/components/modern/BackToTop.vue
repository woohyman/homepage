<template>
  <transition name="fade-scale">
    <button 
      v-show="isVisible" 
      class="back-to-top"
      @click="scrollToTop"
      :title="'返回顶部'"
    >
      <div class="btn-content">
        <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"/>
        </svg>
      </div>
      <div class="progress-ring">
        <svg class="progress-svg" viewBox="0 0 36 36">
          <circle
            class="progress-bg"
            cx="18"
            cy="18"
            r="16"
            fill="none"
            stroke="rgba(255,255,255,0.2)"
            stroke-width="2"
          />
          <circle
            class="progress-bar"
            cx="18"
            cy="18"
            r="16"
            fill="none"
            stroke="white"
            stroke-width="2"
            stroke-linecap="round"
            :stroke-dasharray="circumference"
            :stroke-dashoffset="progressOffset"
            transform="rotate(-90 18 18)"
          />
        </svg>
      </div>
    </button>
  </transition>
</template>

<script>
export default {
  name: 'BackToTop',
  data() {
    return {
      isVisible: false,
      scrollProgress: 0,
      circumference: 2 * Math.PI * 16 // 2πr where r=16
    }
  },
  computed: {
    progressOffset() {
      return this.circumference - (this.scrollProgress / 100) * this.circumference;
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const scrollTop = window.pageYOffset;
      const docHeight = document.documentElement.scrollHeight - window.innerHeight;
      
      // 显示/隐藏按钮
      this.isVisible = scrollTop > 300;
      
      // 计算滚动进度
      this.scrollProgress = (scrollTop / docHeight) * 100;
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    }
  }
}
</script>

<style scoped>
.back-to-top {
  position: fixed;
  bottom: var(--space-8);
  right: var(--space-8);
  width: 56px;
  height: 56px;
  background: var(--gradient-primary);
  border: none;
  border-radius: 50%;
  cursor: pointer;
  z-index: 1000;
  transition: var(--transition-all);
  box-shadow: var(--shadow-lg);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.back-to-top:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-xl);
}

.back-to-top:active {
  transform: translateY(0);
}

.btn-content {
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

.arrow-icon {
  width: 20px;
  height: 20px;
  transition: var(--transition-transform);
}

.back-to-top:hover .arrow-icon {
  transform: translateY(-2px);
}

.progress-ring {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.progress-svg {
  width: 100%;
  height: 100%;
  transform: rotate(-90deg);
}

.progress-bar {
  transition: stroke-dashoffset 0.1s ease;
}

/* 过渡动画 */
.fade-scale-enter-active,
.fade-scale-leave-active {
  transition: all 0.3s var(--ease-out);
}

.fade-scale-enter-from,
.fade-scale-leave-to {
  opacity: 0;
  transform: translateY(20px) scale(0.8);
}

/* 响应式设计 */
@media (max-width: 768px) {
  .back-to-top {
    bottom: var(--space-6);
    right: var(--space-6);
    width: 48px;
    height: 48px;
  }
  
  .arrow-icon {
    width: 18px;
    height: 18px;
  }
}

@media (max-width: 480px) {
  .back-to-top {
    bottom: var(--space-4);
    right: var(--space-4);
    width: 44px;
    height: 44px;
  }
  
  .arrow-icon {
    width: 16px;
    height: 16px;
  }
}

/* 脉冲动画效果 */
.back-to-top::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 50%;
  background: var(--gradient-primary);
  animation: pulse 2s infinite;
  z-index: 0;
}

@keyframes pulse {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.7;
  }
  100% {
    transform: scale(1.2);
    opacity: 0;
  }
}
</style>
