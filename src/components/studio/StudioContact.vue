<template>
  <div class="studio-contact">
    <div class="container">
      <!-- 标题区域 -->
      <div class="section-header">
        <div class="section-badge">
          <span class="badge-icon">📞</span>
          <span>联系我们</span>
        </div>
        <h2 class="section-title">开始您的项目</h2>
        <p class="section-description">
          有项目需求？让我们一起讨论如何实现您的想法，为您提供专业的解决方案
        </p>
      </div>
      
      <!-- 联系内容 -->
      <div class="contact-content">
        <!-- 联系信息 -->
        <div class="contact-info">
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fas fa-envelope"></i>
            </div>
            <div class="contact-details">
              <h3>邮箱联系</h3>
              <p>studio@example.com</p>
              <span>我们会在24小时内回复</span>
            </div>
          </div>
          
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fas fa-phone"></i>
            </div>
            <div class="contact-details">
              <h3>电话咨询</h3>
              <p>+86 138-0000-0000</p>
              <span>工作日 9:00-18:00</span>
            </div>
          </div>
          
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fab fa-weixin"></i>
            </div>
            <div class="contact-details">
              <h3>微信咨询</h3>
              <p>studio_design</p>
              <span>扫码添加微信</span>
            </div>
          </div>
          
          <div class="contact-item">
            <div class="contact-icon">
              <i class="fas fa-map-marker-alt"></i>
            </div>
            <div class="contact-details">
              <h3>工作室地址</h3>
              <p>北京市朝阳区</p>
              <span>欢迎预约实地拜访</span>
            </div>
          </div>
        </div>
        
        <!-- 联系表单 -->
        <div class="contact-form">
          <form @submit.prevent="submitForm">
            <div class="form-row">
              <div class="form-group">
                <label for="name">姓名 *</label>
                <input 
                  type="text" 
                  id="name" 
                  v-model="form.name" 
                  placeholder="请输入您的姓名"
                  required
                >
              </div>
              <div class="form-group">
                <label for="company">公司</label>
                <input 
                  type="text" 
                  id="company" 
                  v-model="form.company" 
                  placeholder="请输入公司名称"
                >
              </div>
            </div>
            
            <div class="form-row">
              <div class="form-group">
                <label for="email">邮箱 *</label>
                <input 
                  type="email" 
                  id="email" 
                  v-model="form.email" 
                  placeholder="请输入邮箱地址"
                  required
                >
              </div>
              <div class="form-group">
                <label for="phone">电话</label>
                <input 
                  type="tel" 
                  id="phone" 
                  v-model="form.phone" 
                  placeholder="请输入联系电话"
                >
              </div>
            </div>
            
            <div class="form-group">
              <label for="project-type">项目类型</label>
              <select id="project-type" v-model="form.projectType">
                <option value="">请选择项目类型</option>
                <option value="desktop">桌面应用开发</option>
                <option value="mobile">移动应用开发</option>
                <option value="web">Web应用开发</option>
                <option value="design">UI/UX设计</option>
                <option value="consulting">技术咨询</option>
                <option value="other">其他</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="budget">预算范围</label>
              <select id="budget" v-model="form.budget">
                <option value="">请选择预算范围</option>
                <option value="5k-10k">5千-1万</option>
                <option value="10k-30k">1万-3万</option>
                <option value="30k-50k">3万-5万</option>
                <option value="50k-100k">5万-10万</option>
                <option value="100k+">10万以上</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="message">项目描述 *</label>
              <textarea 
                id="message" 
                v-model="form.message" 
                placeholder="请详细描述您的项目需求、功能要求、时间安排等"
                rows="5"
                required
              ></textarea>
            </div>
            
            <button type="submit" class="submit-btn" :disabled="isSubmitting">
              <i class="fas fa-paper-plane" v-if="!isSubmitting"></i>
              <i class="fas fa-spinner fa-spin" v-if="isSubmitting"></i>
              <span>{{ isSubmitting ? '发送中...' : '发送消息' }}</span>
            </button>
          </form>
        </div>
      </div>
      
      <!-- 工作流程 -->
      <div class="workflow-section">
        <h3 class="workflow-title">合作流程</h3>
        <div class="workflow-steps">
          <div class="step" v-for="(step, index) in workflowSteps" :key="index">
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
  name: 'StudioContact',
  data() {
    return {
      isSubmitting: false,
      form: {
        name: '',
        company: '',
        email: '',
        phone: '',
        projectType: '',
        budget: '',
        message: ''
      },
      workflowSteps: [
        {
          title: '需求沟通',
          description: '详细了解您的项目需求和期望目标'
        },
        {
          title: '方案制定',
          description: '制定详细的技术方案和项目计划'
        },
        {
          title: '合同签署',
          description: '确定合作细节，签署正式合同'
        },
        {
          title: '项目开发',
          description: '按照计划进行开发，定期汇报进度'
        },
        {
          title: '测试交付',
          description: '全面测试后交付，提供培训和文档'
        },
        {
          title: '后期维护',
          description: '提供技术支持和后期维护服务'
        }
      ]
    }
  },
  methods: {
    async submitForm() {
      this.isSubmitting = true;
      
      try {
        // 模拟发送请求
        await new Promise(resolve => setTimeout(resolve, 2000));
        
        // 显示成功消息
        alert('消息发送成功！我们会尽快与您联系。');
        
        // 重置表单
        this.resetForm();
      } catch (error) {
        alert('发送失败，请稍后重试或直接联系我们。');
      } finally {
        this.isSubmitting = false;
      }
    },
    
    resetForm() {
      this.form = {
        name: '',
        company: '',
        email: '',
        phone: '',
        projectType: '',
        budget: '',
        message: ''
      };
    }
  }
}
</script>

<style scoped>
.studio-contact {
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

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  margin-bottom: 80px;
}

.contact-item {
  display: flex;
  gap: 16px;
  margin-bottom: 32px;
}

.contact-icon {
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

.contact-details h3 {
  font-size: 18px;
  font-weight: 600;
  color: #1a202c;
  margin-bottom: 8px;
}

.contact-details p {
  font-size: 16px;
  color: #667eea;
  font-weight: 500;
  margin-bottom: 4px;
}

.contact-details span {
  font-size: 14px;
  color: #4a5568;
}

.contact-form {
  background: white;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.07);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  margin-bottom: 24px;
}

.form-group label {
  display: block;
  font-size: 14px;
  font-weight: 500;
  color: #1a202c;
  margin-bottom: 8px;
}

.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 12px 16px;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  font-size: 16px;
  transition: all 0.3s ease;
  background: white;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-btn {
  width: 100%;
  padding: 16px 24px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

.submit-btn:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 8px 15px rgba(102, 126, 234, 0.3);
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.workflow-section {
  background: white;
  border-radius: 16px;
  padding: 48px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.07);
}

.workflow-title {
  font-size: 32px;
  font-weight: 700;
  color: #1a202c;
  text-align: center;
  margin-bottom: 48px;
}

.workflow-steps {
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
  .studio-contact {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 32px;
  }
  
  .section-description {
    font-size: 16px;
  }
  
  .contact-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .contact-form {
    padding: 32px 24px;
  }
  
  .form-row {
    grid-template-columns: 1fr;
    gap: 0;
  }
  
  .workflow-section {
    padding: 32px 24px;
  }
  
  .workflow-title {
    font-size: 28px;
  }
  
  .workflow-steps {
    grid-template-columns: 1fr;
    gap: 24px;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 28px;
  }
  
  .contact-item {
    flex-direction: column;
    text-align: center;
    margin-bottom: 24px;
  }
  
  .contact-form {
    padding: 24px 16px;
  }
  
  .workflow-section {
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
:global(.dark) .studio-contact {
  background: #0f172a;
}

:global(.dark) .section-title {
  color: #f1f5f9;
}

:global(.dark) .section-description {
  color: #cbd5e1;
}

:global(.dark) .contact-details h3 {
  color: #f1f5f9;
}

:global(.dark) .contact-details span {
  color: #cbd5e1;
}

:global(.dark) .contact-form {
  background: #1e293b;
}

:global(.dark) .form-group label {
  color: #f1f5f9;
}

:global(.dark) .form-group input,
:global(.dark) .form-group select,
:global(.dark) .form-group textarea {
  background: #334155;
  border-color: #475569;
  color: #f1f5f9;
}

:global(.dark) .form-group input:focus,
:global(.dark) .form-group select:focus,
:global(.dark) .form-group textarea:focus {
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

:global(.dark) .workflow-section {
  background: #1e293b;
}

:global(.dark) .workflow-title {
  color: #f1f5f9;
}

:global(.dark) .step-title {
  color: #f1f5f9;
}

:global(.dark) .step-description {
  color: #cbd5e1;
}
</style>
