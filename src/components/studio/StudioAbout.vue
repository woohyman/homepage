<template>
  <div class="studio-about">
    <div class="container">
      <!-- 标题区域 -->
      <div class="section-header">
        <div class="section-badge">
          <span class="badge-icon">🏢</span>
          <span>关于工作室</span>
        </div>
        <h2 class="section-title">专业团队，创新设计</h2>
        <p class="section-description">
          我们是一支专注于客户端软件设计与开发的创新团队，致力于为客户提供优质的软件解决方案
        </p>
      </div>
      
      <!-- 主要内容 -->
      <div class="about-content">
        <div class="about-text">
          <div class="about-item">
            <div class="about-icon">
              <i class="fas fa-lightbulb"></i>
            </div>
            <div class="about-info">
              <h3>创新设计理念</h3>
              <p>始终保持对最新设计趋势的敏感度，将创新的设计理念融入到每一个项目中，为用户创造卓越的体验。</p>
            </div>
          </div>
          
          <div class="about-item">
            <div class="about-icon">
              <i class="fas fa-desktop"></i>
            </div>
            <div class="about-info">
              <h3>客户端专精</h3>
              <p>专注于桌面应用、移动应用等客户端软件开发，掌握多种开发技术栈，提供跨平台解决方案。</p>
            </div>
          </div>
          
          <div class="about-item">
            <div class="about-icon">
              <i class="fas fa-users"></i>
            </div>
            <div class="about-info">
              <h3>专业团队</h3>
              <p>拥有经验丰富的设计师和开发工程师，团队成员在UI/UX设计、软件架构等领域具有深厚的专业背景。</p>
            </div>
          </div>
          
          <div class="about-item">
            <div class="about-icon">
              <i class="fas fa-award"></i>
            </div>
            <div class="about-info">
              <h3>品质保证</h3>
              <p>严格的质量控制流程，从需求分析到产品交付，每个环节都精益求精，确保交付高质量的软件产品。</p>
            </div>
          </div>
        </div>
        
        <div class="about-visual">
          <div class="team-showcase">
            <div class="showcase-header">
              <h3>我们的优势</h3>
            </div>
            <div class="advantages-grid">
              <div class="advantage-card">
                <div class="advantage-icon">🎨</div>
                <div class="advantage-title">UI/UX设计</div>
                <div class="advantage-desc">专业的界面设计和用户体验优化</div>
              </div>
              <div class="advantage-card">
                <div class="advantage-icon">💻</div>
                <div class="advantage-title">跨平台开发</div>
                <div class="advantage-desc">支持Windows、macOS、Linux等多平台</div>
              </div>
              <div class="advantage-card">
                <div class="advantage-icon">⚡</div>
                <div class="advantage-title">性能优化</div>
                <div class="advantage-desc">高效的代码架构和性能调优</div>
              </div>
              <div class="advantage-card">
                <div class="advantage-icon">🔧</div>
                <div class="advantage-title">定制开发</div>
                <div class="advantage-desc">根据客户需求提供定制化解决方案</div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- 数据统计 -->
      <div class="stats-section">
        <div class="stats-grid">
          <div class="stat-card">
            <div class="stat-number">{{ stats.experience }}</div>
            <div class="stat-label">年开发经验</div>
          </div>
          <div class="stat-card">
            <div class="stat-number">{{ stats.projects }}</div>
            <div class="stat-label">完成项目</div>
          </div>
          <div class="stat-card">
            <div class="stat-number">{{ stats.clients }}</div>
            <div class="stat-label">服务客户</div>
          </div>
          <div class="stat-card">
            <div class="stat-number">{{ stats.satisfaction }}</div>
            <div class="stat-label">客户满意度</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudioAbout',
  data() {
    return {
      stats: {
        experience: '5+',
        projects: '100+',
        clients: '50+',
        satisfaction: '98%'
      }
    }
  }
}
</script>

<style scoped>
.studio-about {
  padding: 80px 0;
  background: #f8fafc;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

.section-header {
  text-align: center;
  margin-bottom: 64px;
}

.section-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: #667eea;
  color: white;
  border-radius: 50px;
  font-size: 14px;
  font-weight: 500;
  margin-bottom: 24px;
}

.badge-icon {
  font-size: 16px;
}

.section-title {
  font-size: 40px;
  font-weight: 700;
  color: #1a202c;
  margin-bottom: 24px;
  line-height: 1.2;
}

.section-description {
  font-size: 18px;
  color: #4a5568;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: start;
  margin-bottom: 80px;
}

.about-item {
  display: flex;
  gap: 16px;
  margin-bottom: 32px;
}

.about-icon {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 24px;
  flex-shrink: 0;
}

.about-info h3 {
  font-size: 20px;
  font-weight: 600;
  color: #1a202c;
  margin-bottom: 8px;
}

.about-info p {
  color: #4a5568;
  line-height: 1.6;
}

.about-visual {
  display: flex;
  justify-content: center;
}

.team-showcase {
  width: 100%;
  max-width: 500px;
  background: white;
  border-radius: 16px;
  padding: 32px;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.showcase-header {
  text-align: center;
  margin-bottom: 24px;
}

.showcase-header h3 {
  font-size: 24px;
  font-weight: 600;
  color: #1a202c;
}

.advantages-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.advantage-card {
  text-align: center;
  padding: 20px;
  border-radius: 12px;
  background: #f7fafc;
  transition: all 0.3s ease;
}

.advantage-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.advantage-icon {
  font-size: 32px;
  margin-bottom: 12px;
}

.advantage-title {
  font-size: 16px;
  font-weight: 600;
  color: #1a202c;
  margin-bottom: 8px;
}

.advantage-desc {
  font-size: 12px;
  color: #4a5568;
  line-height: 1.4;
}

.stats-section {
  background: white;
  border-radius: 16px;
  padding: 40px;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
}

.stat-card {
  text-align: center;
}

.stat-number {
  font-size: 36px;
  font-weight: 700;
  color: #667eea;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 14px;
  color: #4a5568;
  font-weight: 500;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .studio-about {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 32px;
  }
  
  .section-description {
    font-size: 16px;
  }
  
  .about-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .about-item {
    margin-bottom: 24px;
  }
  
  .about-icon {
    width: 50px;
    height: 50px;
    font-size: 20px;
  }
  
  .team-showcase {
    padding: 24px;
  }
  
  .advantages-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 24px;
  }
  
  .stat-number {
    font-size: 28px;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 28px;
  }
  
  .about-item {
    flex-direction: column;
    text-align: center;
    margin-bottom: 20px;
  }
  
  .stats-section {
    padding: 24px;
  }
  
  .stats-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
}

/* 深色主题 */
:global(.dark) .studio-about {
  background: #0f172a;
}

:global(.dark) .section-title {
  color: #f1f5f9;
}

:global(.dark) .section-description {
  color: #cbd5e1;
}

:global(.dark) .about-info h3 {
  color: #f1f5f9;
}

:global(.dark) .about-info p {
  color: #cbd5e1;
}

:global(.dark) .team-showcase {
  background: #1e293b;
}

:global(.dark) .showcase-header h3 {
  color: #f1f5f9;
}

:global(.dark) .advantage-card {
  background: #334155;
}

:global(.dark) .advantage-title {
  color: #f1f5f9;
}

:global(.dark) .advantage-desc {
  color: #cbd5e1;
}

:global(.dark) .stats-section {
  background: #1e293b;
}

:global(.dark) .stat-label {
  color: #cbd5e1;
}
</style>
