<template>
  <div id="app" class="studio-app">
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

.studio-app {
  width: 100%;
  min-height: 100vh;
  background: white;
  overflow-x: hidden;
}

/* 深色主题 */
.studio-app.dark {
  background: #0f172a;
  color: #f1f5f9;
}

/* 深色主题下的导航栏 */
.studio-app.dark .modern-nav {
  background: rgba(15, 23, 42, 0.8);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.studio-app.dark .nav-scrolled {
  background: rgba(15, 23, 42, 0.95);
}

.studio-app.dark .nav-brand {
  color: #f1f5f9;
}

.studio-app.dark .nav-link {
  color: #cbd5e1;
}

.studio-app.dark .nav-link:hover,
.studio-app.dark .nav-link.active {
  color: #667eea;
}

.studio-app.dark .mobile-menu {
  background: rgba(15, 23, 42, 0.95);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.studio-app.dark .mobile-nav-link {
  color: #f1f5f9;
}

.studio-app.dark .mobile-nav-link:hover {
  background: rgba(255, 255, 255, 0.1);
  color: #667eea;
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
