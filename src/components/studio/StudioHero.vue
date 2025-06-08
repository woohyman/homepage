<template>
  <section id="hero" class="studio-hero">
    <!-- 背景动画 -->
    <div class="hero-bg">
      <div class="bg-gradient"></div>
      <div class="floating-shapes">
        <div class="shape shape-1"></div>
        <div class="shape shape-2"></div>
        <div class="shape shape-3"></div>
        <div class="shape shape-4"></div>
      </div>
    </div>
    
    <!-- 粒子效果 -->
    <vue-particles
      color="#ffffff"
      :particleOpacity="0.6"
      linesColor="#ffffff"
      :particlesNumber="isMobile ? 20 : 60"
      shapeType="circle"
      :particleSize="isMobile ? 2 : 4"
      :linesWidth="1"
      :lineLinked="true"
      :lineOpacity="0.3"
      :linesDistance="150"
      :moveSpeed="1"
      :hoverEffect="!isMobile"
      hoverMode="grab"
      :clickEffect="false"
    />
    
    <!-- 主要内容 -->
    <div class="hero-content">
      <div class="container">
        <div class="hero-grid">
          <!-- 左侧内容 -->
          <div class="hero-text">
            <div class="hero-badge animate-fade-in">
              <span class="badge-icon">🎨</span>
              <span>专业设计工作室</span>
            </div>
            
            <h1 class="hero-title animate-slide-up">
              <span class="title-line">{{ info.name }}</span>
              <span class="title-line gradient-text">{{ info.slogan }}</span>
            </h1>
            
            <p class="hero-description animate-slide-up">
              {{ info.description }}
            </p>
            
            <div class="hero-stats animate-slide-up">
              <div class="stat-item">
                <div class="stat-number">{{ info.founded }}</div>
                <div class="stat-label">成立年份</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">{{ info.projects }}</div>
                <div class="stat-label">完成项目</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">{{ info.clients }}</div>
                <div class="stat-label">服务客户</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">{{ info.downloads }}</div>
                <div class="stat-label">软件下载</div>
              </div>
            </div>
            
            <div class="hero-actions animate-scale-in">
              <a href="#products" class="btn btn-primary">
                <span>查看作品</span>
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path d="M7 17L17 7M17 7H7M17 7V17"/>
                </svg>
              </a>
              <a href="#contact" class="btn btn-glass">
                <span>联系合作</span>
              </a>
            </div>
          </div>
          
          <!-- 右侧展示 -->
          <div class="hero-showcase">
            <div class="showcase-container animate-float">
              <div class="software-preview">
                <div class="window-frame">
                  <div class="window-header">
                    <div class="window-controls">
                      <span class="control close"></span>
                      <span class="control minimize"></span>
                      <span class="control maximize"></span>
                    </div>
                    <div class="window-title">客户端应用</div>
                  </div>
                  <div class="window-content">
                    <div class="app-interface">
                      <div class="interface-header">
                        <div class="logo">🎨</div>
                        <div class="app-name">设计工具</div>
                      </div>
                      <div class="interface-body">
                        <div class="sidebar">
                          <div class="menu-item active">项目</div>
                          <div class="menu-item">设计</div>
                          <div class="menu-item">导出</div>
                        </div>
                        <div class="main-area">
                          <div class="canvas">
                            <div class="design-element"></div>
                            <div class="design-element small"></div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            
            <!-- 技术标签 -->
            <div class="tech-tags">
              <div class="tech-tag" v-for="(tech, index) in info.specialties" :key="index">
                <span>{{ tech }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 滚动指示器 -->
    <div class="scroll-indicator" @click="scrollToNext">
      <div class="scroll-mouse">
        <div class="scroll-wheel"></div>
      </div>
      <span class="scroll-text">了解更多</span>
    </div>
  </section>
</template>

<script>
export default {
  name: 'StudioHero',
  props: {
    info: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      isMobile: false
    }
  },
  mounted() {
    this.checkMobile();
    window.addEventListener('resize', this.checkMobile);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.checkMobile);
  },
  methods: {
    checkMobile() {
      this.isMobile = window.innerWidth <= 768;
    },
    scrollToNext() {
      const nextSection = document.querySelector('#about');
      if (nextSection) {
        nextSection.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
}
</script>

<style scoped>
.studio-hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
}

.bg-gradient {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  opacity: 0.9;
}

.floating-shapes {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.shape {
  position: absolute;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  animation: float 6s ease-in-out infinite;
}

.shape-1 {
  width: 80px;
  height: 80px;
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}

.shape-2 {
  width: 120px;
  height: 120px;
  top: 60%;
  right: 15%;
  animation-delay: 2s;
}

.shape-3 {
  width: 60px;
  height: 60px;
  bottom: 30%;
  left: 20%;
  animation-delay: 4s;
}

.shape-4 {
  width: 100px;
  height: 100px;
  top: 10%;
  right: 30%;
  animation-delay: 1s;
}

.hero-content {
  position: relative;
  z-index: 10;
  width: 100%;
  padding: 120px 0 80px;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

.hero-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}

.hero-text {
  color: white;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 50px;
  font-size: 14px;
  font-weight: 500;
  margin-bottom: 24px;
}

.badge-icon {
  font-size: 16px;
}

.hero-title {
  font-size: 48px;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 24px;
}

.title-line {
  display: block;
}

.gradient-text {
  background: linear-gradient(45deg, #fff, #e3f2fd);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: 18px;
  line-height: 1.6;
  opacity: 0.9;
  margin-bottom: 32px;
  max-width: 500px;
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
  margin-bottom: 40px;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 4px;
}

.stat-label {
  font-size: 12px;
  opacity: 0.8;
}

.hero-actions {
  display: flex;
  gap: 16px;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  border: none;
  border-radius: 12px;
  font-size: 16px;
  font-weight: 500;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-primary {
  background: white;
  color: #667eea;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
}

.btn-glass {
  background: rgba(255, 255, 255, 0.1);
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
}

.btn-glass:hover {
  background: rgba(255, 255, 255, 0.2);
}

.hero-showcase {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 32px;
}

.showcase-container {
  position: relative;
}

.software-preview {
  width: 400px;
  height: 300px;
}

.window-frame {
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
}

.window-header {
  height: 40px;
  background: #f5f5f5;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 16px;
  border-bottom: 1px solid #e0e0e0;
}

.window-controls {
  display: flex;
  gap: 8px;
}

.control {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.control.close {
  background: #ff5f57;
}

.control.minimize {
  background: #ffbd2e;
}

.control.maximize {
  background: #28ca42;
}

.window-title {
  font-size: 14px;
  font-weight: 500;
  color: #666;
}

.window-content {
  height: calc(100% - 40px);
  padding: 16px;
}

.app-interface {
  height: 100%;
  display: flex;
  flex-direction: column;
}

.interface-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 16px;
}

.logo {
  font-size: 24px;
}

.app-name {
  font-size: 16px;
  font-weight: 600;
  color: #333;
}

.interface-body {
  flex: 1;
  display: flex;
  gap: 16px;
}

.sidebar {
  width: 80px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.menu-item {
  padding: 8px 12px;
  font-size: 12px;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.menu-item.active {
  background: #667eea;
  color: white;
}

.menu-item:not(.active) {
  background: #f0f0f0;
  color: #666;
}

.main-area {
  flex: 1;
  background: #fafafa;
  border-radius: 8px;
  padding: 16px;
  position: relative;
}

.canvas {
  width: 100%;
  height: 100%;
  position: relative;
}

.design-element {
  position: absolute;
  background: linear-gradient(45deg, #667eea, #764ba2);
  border-radius: 8px;
}

.design-element:first-child {
  width: 60px;
  height: 40px;
  top: 20px;
  left: 20px;
}

.design-element.small {
  width: 30px;
  height: 30px;
  top: 40px;
  right: 30px;
  border-radius: 50%;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: center;
}

.tech-tag {
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  color: white;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.3s ease;
}

.tech-tag:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
}

.scroll-indicator {
  position: absolute;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: white;
  cursor: pointer;
  opacity: 0.8;
  transition: opacity 0.3s ease;
  z-index: 10;
}

.scroll-indicator:hover {
  opacity: 1;
}

.scroll-mouse {
  width: 24px;
  height: 40px;
  border: 2px solid white;
  border-radius: 12px;
  position: relative;
}

.scroll-wheel {
  width: 4px;
  height: 8px;
  background: white;
  border-radius: 2px;
  position: absolute;
  top: 6px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 2s infinite;
}

@keyframes scroll {
  0% { opacity: 0; transform: translateX(-50%) translateY(0); }
  50% { opacity: 1; }
  100% { opacity: 0; transform: translateX(-50%) translateY(16px); }
}

.scroll-text {
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 1px;
  text-transform: uppercase;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-20px); }
}

/* 响应式设计 */
@media (max-width: 768px) {
  .hero-grid {
    grid-template-columns: 1fr;
    gap: 32px;
    text-align: center;
  }
  
  .hero-title {
    font-size: 36px;
  }
  
  .hero-description {
    font-size: 16px;
  }
  
  .hero-stats {
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
  }
  
  .hero-actions {
    justify-content: center;
    flex-wrap: wrap;
  }
  
  .software-preview {
    width: 320px;
    height: 240px;
  }
  
  .tech-tags {
    max-width: 300px;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 28px;
  }
  
  .hero-stats {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .software-preview {
    width: 280px;
    height: 200px;
  }
}

/* 深色主题 */
:global(.dark) .studio-hero {
  background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
}

:global(.dark) .bg-gradient {
  background: linear-gradient(135deg, #334155 0%, #1e293b 100%);
}

:global(.dark) .hero-badge {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

:global(.dark) .window-frame {
  background: rgba(30, 41, 59, 0.95);
}

:global(.dark) .window-header {
  background: #1e293b;
  border-bottom: 1px solid #334155;
}

:global(.dark) .window-title {
  color: #cbd5e1;
}

:global(.dark) .app-name {
  color: #f1f5f9;
}

:global(.dark) .menu-item:not(.active) {
  background: #334155;
  color: #cbd5e1;
}

:global(.dark) .main-area {
  background: #0f172a;
}

:global(.dark) .tech-tag {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

:global(.dark) .tech-tag:hover {
  background: rgba(255, 255, 255, 0.1);
}
</style>
