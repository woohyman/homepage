<template>
  <div class="studio-services">
    <div class="container">
      <!-- 标题区域 -->
      <div class="section-header">
        <div class="section-badge">
          <span class="badge-icon">🛠️</span>
          <span>我们的服务</span>
        </div>
        <h2 class="section-title">专业的客户端开发服务</h2>
        <p class="section-description">
          从UI/UX设计到完整的客户端应用开发，我们提供全方位的软件开发服务
        </p>
      </div>
      
      <!-- 服务网格 -->
      <div class="services-grid">
        <div class="service-card" v-for="(service, index) in services" :key="index">
          <div class="service-icon">
            <i :class="service.icon"></i>
          </div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-description">{{ service.description }}</p>
          <ul class="service-features">
            <li v-for="(feature, idx) in service.features" :key="idx">{{ feature }}</li>
          </ul>
          <div class="service-price">
            <span class="price-label">起价</span>
            <span class="price-value">{{ service.price }}</span>
          </div>
        </div>
      </div>
      
      <!-- 开发流程 -->
      <div class="process-section">
        <h3 class="process-title">开发流程</h3>
        <div class="process-steps">
          <div class="step" v-for="(step, index) in processSteps" :key="index">
            <div class="step-number">{{ index + 1 }}</div>
            <div class="step-content">
              <h4 class="step-title">{{ step.title }}</h4>
              <p class="step-description">{{ step.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudioServices',
  data() {
    return {
      services: [
        {
          icon: 'fas fa-paint-brush',
          title: 'UI/UX设计',
          description: '专业的用户界面设计和用户体验优化，创造直观美观的软件界面。',
          features: [
            '界面原型设计',
            '交互设计',
            '视觉设计',
            '用户体验优化',
            '设计规范制定'
          ],
          price: '¥5,000'
        },
        {
          icon: 'fas fa-desktop',
          title: '桌面应用开发',
          description: '跨平台桌面应用开发，支持Windows、macOS、Linux等操作系统。',
          features: [
            'Electron应用开发',
            'Qt应用开发',
            'WPF应用开发',
            '原生应用开发',
            '性能优化'
          ],
          price: '¥15,000'
        },
        {
          icon: 'fas fa-mobile-alt',
          title: '移动应用开发',
          description: '原生和跨平台移动应用开发，为iOS和Android平台提供优质应用。',
          features: [
            'React Native开发',
            'Flutter开发',
            '原生iOS开发',
            '原生Android开发',
            '应用商店上架'
          ],
          price: '¥20,000'
        },
        {
          icon: 'fas fa-code',
          title: '定制开发',
          description: '根据客户特定需求提供定制化软件开发解决方案。',
          features: [
            '需求分析',
            '技术选型',
            '架构设计',
            '功能开发',
            '测试部署'
          ],
          price: '面议'
        },
        {
          icon: 'fas fa-cogs',
          title: '软件维护',
          description: '提供软件后期维护、更新升级和技术支持服务。',
          features: [
            'Bug修复',
            '功能更新',
            '性能优化',
            '技术支持',
            '版本升级'
          ],
          price: '¥2,000/月'
        },
        {
          icon: 'fas fa-graduation-cap',
          title: '技术咨询',
          description: '提供技术咨询、架构设计和开发指导服务。',
          features: [
            '技术选型建议',
            '架构设计指导',
            '代码审查',
            '性能分析',
            '团队培训'
          ],
          price: '¥800/小时'
        }
      ],
      processSteps: [
        {
          title: '需求分析',
          description: '深入了解客户需求，制定详细的项目规划和技术方案。'
        },
        {
          title: '设计阶段',
          description: '进行UI/UX设计，创建原型和设计稿，确保用户体验。'
        },
        {
          title: '开发实现',
          description: '按照设计稿进行功能开发，采用敏捷开发模式。'
        },
        {
          title: '测试优化',
          description: '全面测试软件功能，优化性能，确保质量。'
        },
        {
          title: '交付部署',
          description: '项目交付和部署，提供使用培训和技术文档。'
        },
        {
          title: '后期维护',
          description: '提供后期维护支持，及时响应客户需求。'
        }
      ]
    }
  }
}
</script>

<style scoped>
.studio-services {
  padding: 80px 0;
  background: white;
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

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 32px;
  margin-bottom: 80px;
}

.service-card {
  background: #f8fafc;
  padding: 32px;
  border-radius: 16px;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.service-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
  border-color: #667eea;
}

.service-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 24px;
  color: white;
  font-size: 32px;
}

.service-title {
  font-size: 24px;
  font-weight: 600;
  color: #1a202c;
  margin-bottom: 16px;
  text-align: center;
}

.service-description {
  color: #4a5568;
  line-height: 1.6;
  margin-bottom: 24px;
  text-align: center;
}

.service-features {
  list-style: none;
  margin-bottom: 24px;
}

.service-features li {
  padding: 8px 0;
  color: #2d3748;
  position: relative;
  padding-left: 24px;
}

.service-features li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #667eea;
  font-weight: 600;
}

.service-price {
  text-align: center;
  padding-top: 24px;
  border-top: 1px solid #e2e8f0;
}

.price-label {
  display: block;
  font-size: 14px;
  color: #4a5568;
  margin-bottom: 8px;
}

.price-value {
  font-size: 24px;
  font-weight: 700;
  color: #667eea;
}

.process-section {
  background: #f8fafc;
  border-radius: 16px;
  padding: 48px;
}

.process-title {
  font-size: 32px;
  font-weight: 700;
  color: #1a202c;
  text-align: center;
  margin-bottom: 48px;
}

.process-steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 32px;
}

.step {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.step-number {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  flex-shrink: 0;
}

.step-content {
  flex: 1;
}

.step-title {
  font-size: 18px;
  font-weight: 600;
  color: #1a202c;
  margin-bottom: 8px;
}

.step-description {
  color: #4a5568;
  line-height: 1.6;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .studio-services {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 32px;
  }
  
  .section-description {
    font-size: 16px;
  }
  
  .services-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .service-card {
    padding: 24px;
  }
  
  .service-icon {
    width: 60px;
    height: 60px;
    font-size: 24px;
  }
  
  .service-title {
    font-size: 20px;
  }
  
  .process-section {
    padding: 32px 24px;
  }
  
  .process-title {
    font-size: 28px;
  }
  
  .process-steps {
    grid-template-columns: 1fr;
    gap: 24px;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 28px;
  }
  
  .service-card {
    padding: 20px;
  }
  
  .process-section {
    padding: 24px 16px;
  }
  
  .step {
    flex-direction: column;
    text-align: center;
  }
  
  .step-number {
    margin: 0 auto 16px;
  }
}

/* 深色主题 */
:global(.dark) .studio-services {
  background: #0f172a;
}

:global(.dark) .section-title {
  color: #f1f5f9;
}

:global(.dark) .section-description {
  color: #cbd5e1;
}

:global(.dark) .service-card {
  background: #1e293b;
}

:global(.dark) .service-title {
  color: #f1f5f9;
}

:global(.dark) .service-description {
  color: #cbd5e1;
}

:global(.dark) .service-features li {
  color: #f1f5f9;
}

:global(.dark) .process-section {
  background: #1e293b;
}

:global(.dark) .process-title {
  color: #f1f5f9;
}

:global(.dark) .step-title {
  color: #f1f5f9;
}

:global(.dark) .step-description {
  color: #cbd5e1;
}
</style>
