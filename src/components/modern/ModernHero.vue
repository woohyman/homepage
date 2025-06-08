<template>
  <section id="hero" class="hero-section">
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
              <span class="badge-icon">👋</span>
              <span>Hello, I'm</span>
            </div>
            
            <h1 class="hero-title animate-slide-up">
              <span class="title-line">{{ info.name }}</span>
              <span class="title-line gradient-text">{{ info.job }}</span>
            </h1>
            
            <p class="hero-description animate-slide-up">
              {{ info.description || '热爱技术，专注于创造优秀的用户体验和高质量的代码。' }}
            </p>
            
            <div class="hero-stats animate-slide-up">
              <div class="stat-item">
                <div class="stat-number">{{ info.experience || '3+' }}</div>
                <div class="stat-label">年经验</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">{{ info.projects || '50+' }}</div>
                <div class="stat-label">项目完成</div>
              </div>
              <div class="stat-item">
                <div class="stat-number">{{ info.clients || '20+' }}</div>
                <div class="stat-label">满意客户</div>
              </div>
            </div>
            
            <div class="hero-actions animate-scale-in">
              <a href="#projects" class="btn btn-primary">
                <span>查看作品</span>
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path d="M7 17L17 7M17 7H7M17 7V17"/>
                </svg>
              </a>
              <a href="#contact" class="btn btn-glass">
                <span>联系我</span>
              </a>
            </div>
          </div>
          
          <!-- 右侧头像 -->
          <div class="hero-avatar">
            <div class="avatar-container animate-float">
              <div class="avatar-ring"></div>
              <div class="avatar-image">
                <img :src="avatarUrl" :alt="info.name" />
              </div>
              <div class="avatar-status">
                <div class="status-dot"></div>
                <span>Available for work</span>
              </div>
            </div>
            
            <!-- 装饰元素 -->
            <div class="avatar-decorations">
              <div class="decoration decoration-1">
                <span>💻</span>
              </div>
              <div class="decoration decoration-2">
                <span>🎨</span>
              </div>
              <div class="decoration decoration-3">
                <span>⚡</span>
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
      <span class="scroll-text">Scroll Down</span>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ModernHero',
  props: {
    info: {
      type: Object,
      default: () => ({
        name: 'Your Name',
        job: 'Full Stack Developer',
        description: '热爱技术，专注于创造优秀的用户体验和高质量的代码。',
        experience: '3+',
        projects: '50+',
        clients: '20+'
      })
    }
  },
  data() {
    return {
      isMobile: false,
      avatarUrl: require('@/common/images/avator.jpg')
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
.hero-section {
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
  background: var(--gradient-primary);
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
  padding: var(--space-20) 0;
}

.hero-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-16);
  align-items: center;
}

.hero-text {
  color: white;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2) var(--space-4);
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: var(--radius-full);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  margin-bottom: var(--space-6);
}

.badge-icon {
  font-size: var(--text-base);
  animation: wave 2s ease-in-out infinite;
}

@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(20deg); }
  75% { transform: rotate(-20deg); }
}

.hero-title {
  font-size: var(--text-6xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  margin-bottom: var(--space-6);
}

.title-line {
  display: block;
}

.hero-description {
  font-size: var(--text-xl);
  line-height: var(--leading-relaxed);
  opacity: 0.9;
  margin-bottom: var(--space-8);
  max-width: 500px;
}

.hero-stats {
  display: flex;
  gap: var(--space-8);
  margin-bottom: var(--space-10);
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: var(--text-3xl);
  font-weight: var(--font-bold);
  margin-bottom: var(--space-1);
}

.stat-label {
  font-size: var(--text-sm);
  opacity: 0.8;
}

.hero-actions {
  display: flex;
  gap: var(--space-4);
}

.hero-avatar {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.avatar-container {
  position: relative;
  z-index: 2;
}

.avatar-ring {
  position: absolute;
  top: -20px;
  left: -20px;
  right: -20px;
  bottom: -20px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  animation: rotate 20s linear infinite;
}

.avatar-ring::before {
  content: '';
  position: absolute;
  top: -4px;
  left: 50%;
  transform: translateX(-50%);
  width: 8px;
  height: 8px;
  background: white;
  border-radius: 50%;
  box-shadow: 0 0 20px rgba(255, 255, 255, 0.8);
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.avatar-image {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid rgba(255, 255, 255, 0.3);
  box-shadow: var(--shadow-2xl);
}

.avatar-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.avatar-status {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2) var(--space-4);
  background: rgba(16, 185, 129, 0.9);
  backdrop-filter: blur(10px);
  border-radius: var(--radius-full);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  color: white;
}

.status-dot {
  width: 8px;
  height: 8px;
  background: white;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

.avatar-decorations {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
}

.decoration {
  position: absolute;
  width: 60px;
  height: 60px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: var(--text-2xl);
  animation: float 4s ease-in-out infinite;
}

.decoration-1 {
  top: 10%;
  left: 10%;
  animation-delay: 0s;
}

.decoration-2 {
  top: 20%;
  right: 10%;
  animation-delay: 1s;
}

.decoration-3 {
  bottom: 20%;
  left: 20%;
  animation-delay: 2s;
}

.scroll-indicator {
  position: absolute;
  bottom: var(--space-8);
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-2);
  color: white;
  cursor: pointer;
  opacity: 0.8;
  transition: var(--transition-opacity);
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
  font-size: var(--text-xs);
  font-weight: var(--font-medium);
  letter-spacing: 1px;
  text-transform: uppercase;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .hero-grid {
    grid-template-columns: 1fr;
    gap: var(--space-8);
    text-align: center;
  }
  
  .hero-title {
    font-size: var(--text-4xl);
  }
  
  .hero-description {
    font-size: var(--text-lg);
  }
  
  .hero-stats {
    justify-content: center;
    gap: var(--space-6);
  }
  
  .hero-actions {
    justify-content: center;
    flex-wrap: wrap;
  }
  
  .avatar-image {
    width: 250px;
    height: 250px;
  }
  
  .decoration {
    width: 50px;
    height: 50px;
    font-size: var(--text-lg);
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: var(--text-3xl);
  }
  
  .hero-stats {
    gap: var(--space-4);
  }
  
  .avatar-image {
    width: 200px;
    height: 200px;
  }
}
</style>
