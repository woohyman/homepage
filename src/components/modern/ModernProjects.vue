<template>
  <div class="modern-projects">
    <div class="container">
      <!-- 标题区域 -->
      <div class="section-header">
        <div class="header-badge animate-fade-in">
          <span class="badge-icon">💼</span>
          <span>我的作品</span>
        </div>
        <h2 class="section-title animate-slide-up">
          精选<span class="gradient-text">项目展示</span>
        </h2>
        <p class="section-description animate-slide-up">
          这里展示了我最近完成的一些项目，涵盖了前端开发、移动应用和全栈解决方案
        </p>
      </div>
      
      <!-- 项目网格 -->
      <div class="projects-grid">
        <div 
          v-for="(project, index) in projects" 
          :key="index"
          class="project-card animate-scale-in"
          :style="{ animationDelay: `${index * 0.1}s` }"
          @click="handleProjectClick(project)"
        >
          <!-- 项目图片 -->
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
            <div class="image-overlay">
              <div class="overlay-content">
                <button class="view-btn">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                    <path d="M7 17L17 7M17 7H7M17 7V17"/>
                  </svg>
                  <span>{{ project.title === '应用商店' ? '立即下载' : '查看详情' }}</span>
                </button>
              </div>
            </div>
          </div>
          
          <!-- 项目信息 -->
          <div class="project-info">
            <div class="project-header">
              <h3 class="project-title">{{ project.title }}</h3>
              <div class="project-status" :class="project.status">
                {{ getStatusText(project.status) }}
              </div>
            </div>
            
            <p class="project-description">{{ project.description }}</p>
            
            <!-- 技术栈 -->
            <div class="tech-stack">
              <span 
                v-for="tech in project.technologies" 
                :key="tech"
                class="tech-tag"
              >
                {{ tech }}
              </span>
            </div>
            
            <!-- 项目链接 -->
            <div class="project-links">
              <a 
                v-if="project.github" 
                :href="project.github" 
                target="_blank"
                class="project-link"
                title="GitHub"
              >
                <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
              </a>
              <a 
                v-if="project.demo" 
                :href="project.demo" 
                target="_blank"
                class="project-link"
                title="在线演示"
              >
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path d="M18 13v6a2 2 0 01-2 2H5a2 2 0 01-2-2V8a2 2 0 012-2h6M15 3h6v6M10 14L21 3"/>
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
      
      <!-- 查看更多按钮 -->
      <div class="section-footer">
        <a href="#" class="btn btn-primary">
          <span>查看更多项目</span>
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path d="M5 12h14M12 5l7 7-7 7"/>
          </svg>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModernProjects',
  data() {
    return {
      projects: [
        {
          title: '应用商店',
          description: '功能完整的Android应用商店，支持应用下载、更新管理、用户评价等功能。',
          image: require('@/common/images/project1.jpg'),
          link: 'https://fbxdadsofwvfktbcbbos.supabase.co/storage/v1/object/public/apk//appstore_demo.apk',
          technologies: ['Android', 'Java', 'Firebase', 'Material Design'],
          status: 'completed',
          github: 'https://github.com/yourusername/app-store',
          demo: null
        },
        {
          title: '博客管理系统',
          description: '现代化的个人博客管理系统，支持Markdown编辑、标签分类、评论系统等。',
          image: require('@/common/images/project2.jpg'),
          link: 'https://github.com/yourusername/blog-system',
          technologies: ['React', 'Node.js', 'MongoDB', 'Express'],
          status: 'in-progress',
          github: 'https://github.com/yourusername/blog-system',
          demo: 'https://blog-demo.com'
        },
        {
          title: '任务管理平台',
          description: '团队协作任务管理工具，支持项目管理、团队协作、进度跟踪等功能。',
          image: require('@/common/images/project3.jpg'),
          link: 'https://github.com/yourusername/task-manager',
          technologies: ['Vue.js', 'Spring Boot', 'PostgreSQL', 'Docker'],
          status: 'completed',
          github: 'https://github.com/yourusername/task-manager',
          demo: 'https://task-demo.com'
        },
        {
          title: '数据可视化平台',
          description: '企业级数据分析可视化平台，支持多种图表类型、实时数据更新。',
          image: require('@/common/images/project4.jpg'),
          link: 'https://github.com/yourusername/data-visualization',
          technologies: ['D3.js', 'Python', 'Flask', 'Redis'],
          status: 'planning',
          github: 'https://github.com/yourusername/data-viz',
          demo: 'https://dataviz-demo.com'
        }
      ]
    }
  },
  methods: {
    handleProjectClick(project) {
      // 第一个项目（应用商店）直接下载
      if (project.title === '应用商店') {
        if (project.link) {
          const link = document.createElement('a');
          link.href = project.link;
          link.download = 'appstore_demo.apk';
          link.style.display = 'none';
          document.body.appendChild(link);
          link.click();
          document.body.removeChild(link);
        }
        return;
      }
      
      // 其他项目打开链接
      if (project.link) {
        window.open(project.link, '_blank');
      }
    },
    getStatusText(status) {
      const statusMap = {
        'completed': '已完成',
        'in-progress': '进行中',
        'planning': '规划中'
      };
      return statusMap[status] || '未知';
    }
  }
}
</script>

<style scoped>
.modern-projects {
  padding: var(--space-20) 0;
  background: var(--gray-50);
}

.section-header {
  text-align: center;
  margin-bottom: var(--space-16);
}

.header-badge {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2) var(--space-4);
  background: var(--glass-bg);
  backdrop-filter: blur(10px);
  border: 1px solid var(--glass-border);
  border-radius: var(--radius-full);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  color: var(--primary);
  margin-bottom: var(--space-6);
}

.badge-icon {
  font-size: var(--text-base);
}

.section-title {
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  color: var(--gray-900);
  margin-bottom: var(--space-6);
}

.section-description {
  font-size: var(--text-xl);
  color: var(--gray-600);
  max-width: 600px;
  margin: 0 auto;
  line-height: var(--leading-relaxed);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: var(--space-8);
  margin-bottom: var(--space-16);
}

.project-card {
  background: white;
  border-radius: var(--radius-xl);
  overflow: hidden;
  box-shadow: var(--shadow);
  transition: var(--transition-all);
  cursor: pointer;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-xl);
}

.project-image {
  position: relative;
  height: 240px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: var(--transition-transform);
}

.project-card:hover .project-image img {
  transform: scale(1.05);
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: var(--transition-opacity);
}

.project-card:hover .image-overlay {
  opacity: 1;
}

.view-btn {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-3) var(--space-6);
  background: white;
  color: var(--gray-900);
  border: none;
  border-radius: var(--radius-lg);
  font-weight: var(--font-medium);
  cursor: pointer;
  transition: var(--transition-all);
}

.view-btn:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

.project-info {
  padding: var(--space-6);
}

.project-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: var(--space-4);
}

.project-title {
  font-size: var(--text-xl);
  font-weight: var(--font-semibold);
  color: var(--gray-900);
}

.project-status {
  padding: var(--space-1) var(--space-3);
  border-radius: var(--radius-full);
  font-size: var(--text-xs);
  font-weight: var(--font-medium);
}

.project-status.completed {
  background: rgba(16, 185, 129, 0.1);
  color: var(--accent);
}

.project-status.in-progress {
  background: rgba(245, 158, 11, 0.1);
  color: var(--secondary);
}

.project-status.planning {
  background: rgba(99, 102, 241, 0.1);
  color: var(--primary);
}

.project-description {
  color: var(--gray-600);
  line-height: var(--leading-relaxed);
  margin-bottom: var(--space-4);
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
  margin-bottom: var(--space-4);
}

.tech-tag {
  padding: var(--space-1) var(--space-3);
  background: var(--gray-100);
  color: var(--gray-700);
  border-radius: var(--radius);
  font-size: var(--text-xs);
  font-weight: var(--font-medium);
}

.project-links {
  display: flex;
  gap: var(--space-3);
}

.project-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  background: var(--gray-100);
  color: var(--gray-600);
  border-radius: var(--radius);
  text-decoration: none;
  transition: var(--transition-all);
}

.project-link:hover {
  background: var(--primary);
  color: white;
  transform: translateY(-1px);
}

.section-footer {
  text-align: center;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .modern-projects {
    padding: var(--space-16) 0;
  }
  
  .section-title {
    font-size: var(--text-4xl);
  }
  
  .section-description {
    font-size: var(--text-lg);
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
    gap: var(--space-6);
  }
  
  .project-image {
    height: 200px;
  }
  
  .project-info {
    padding: var(--space-4);
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: var(--text-3xl);
  }
  
  .projects-grid {
    gap: var(--space-4);
  }
  
  .project-header {
    flex-direction: column;
    align-items: flex-start;
    gap: var(--space-2);
  }
}
</style>
