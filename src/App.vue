<template>
  <div id="app" class="modern-app">
    <ModernNav />
    <router-view/>
    <BackToTop />
  </div>
</template>

<script>
import ModernNav from '@/components/modern/ModernNav.vue'
import BackToTop from '@/components/modern/BackToTop.vue'

export default {
  name: 'App',
  components: {
    ModernNav,
    BackToTop
  }
}
</script>

<style>
@import './styles/modern-design.css';
@import './styles/performance.css';

.modern-app {
  width: 100%;
  min-height: 100vh;
  background: var(--gray-50);
  overflow-x: hidden;
}

/* 深色主题 */
.modern-app.dark {
  background: var(--gray-900);
  color: var(--gray-100);
}

/* 页面过渡动画 */
.page-enter-active,
.page-leave-active {
  transition: opacity 0.3s ease;
}

.page-enter-from,
.page-leave-to {
  opacity: 0;
}

/* 滚动行为优化 */
html {
  scroll-behavior: smooth;
  scroll-padding-top: 80px;
}

/* 选择文本样式 */
::selection {
  background: var(--primary);
  color: white;
}

/* 焦点样式 */
:focus-visible {
  outline: 2px solid var(--primary);
  outline-offset: 2px;
}
</style>
