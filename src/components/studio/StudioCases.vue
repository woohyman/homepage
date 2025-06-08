<template>
  <div class="studio-cases">
    <div class="container">
      <!-- 标题区域 -->
      <div class="section-header">
        <div class="section-badge">
          <span class="badge-icon">🏆</span>
          <span>客户案例</span>
        </div>
        <h2 class="section-title">成功案例展示</h2>
        <p class="section-description">
          我们为各行业客户提供了优质的软件解决方案，获得了客户的一致好评
        </p>
      </div>
      
      <!-- 案例网格 -->
      <div class="cases-grid">
        <div 
          v-for="(caseItem, index) in cases" 
          :key="index"
          class="case-card"
        >
          <div class="case-image">
            <div class="case-placeholder">
              <i :class="caseItem.icon"></i>
            </div>
          </div>
          
          <div class="case-info">
            <div class="case-header">
              <h3 class="case-title">{{ caseItem.title }}</h3>
              <span class="case-industry">{{ caseItem.industry }}</span>
            </div>
            
            <p class="case-description">{{ caseItem.description }}</p>
            
            <div class="case-features">
              <div class="feature-item" v-for="feature in caseItem.features" :key="feature">
                <i class="fas fa-check"></i>
                <span>{{ feature }}</span>
              </div>
            </div>
            
            <div class="case-results">
              <div class="result-item" v-for="result in caseItem.results" :key="result.label">
                <div class="result-value">{{ result.value }}</div>
                <div class="result-label">{{ result.label }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- 客户评价 -->
      <div class="testimonials-section">
        <h3 class="testimonials-title">客户评价</h3>
        <div class="testimonials-grid">
          <div 
            v-for="(testimonial, index) in testimonials" 
            :key="index"
            class="testimonial-card"
          >
            <div class="testimonial-content">
              <div class="quote-icon">
                <i class="fas fa-quote-left"></i>
              </div>
              <p class="testimonial-text">{{ testimonial.content }}</p>
            </div>
            <div class="testimonial-author">
              <div class="author-avatar">
                <i class="fas fa-user"></i>
              </div>
              <div class="author-info">
                <div class="author-name">{{ testimonial.author }}</div>
                <div class="author-position">{{ testimonial.position }}</div>
                <div class="author-company">{{ testimonial.company }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudioCases',
  data() {
    return {
      cases: [
        {
          title: '企业管理系统',
          industry: '制造业',
          description: '为大型制造企业开发的综合管理系统，包含生产管理、库存管理、财务管理等模块。',
          icon: 'fas fa-industry',
          features: [
            '生产流程数字化',
            '实时数据监控',
            '智能报表分析',
            '移动端支持'
          ],
          results: [
            { label: '效率提升', value: '40%' },
            { label: '成本降低', value: '25%' },
            { label: '用户满意度', value: '95%' }
          ]
        },
        {
          title: '在线教育平台',
          industry: '教育行业',
          description: '为教育机构打造的在线学习平台，支持直播教学、作业管理、学习进度跟踪等功能。',
          icon: 'fas fa-graduation-cap',
          features: [
            '高清视频直播',
            '互动白板',
            '作业自动批改',
            '学习数据分析'
          ],
          results: [
            { label: '学生活跃度', value: '85%' },
            { label: '教学效果', value: '90%' },
            { label: '平台稳定性', value: '99.9%' }
          ]
        },
        {
          title: '医疗信息系统',
          industry: '医疗健康',
          description: '为医院开发的综合信息管理系统，实现了患者信息管理、诊疗流程优化、药品管理等功能。',
          icon: 'fas fa-hospital',
          features: [
            '电子病历管理',
            '智能诊断辅助',
            '药品库存管理',
            '数据安全保护'
          ],
          results: [
            { label: '诊疗效率', value: '60%' },
            { label: '错误率降低', value: '80%' },
            { label: '患者满意度', value: '92%' }
          ]
        },
        {
          title: '电商管理平台',
          industry: '电子商务',
          description: '为电商企业开发的全渠道管理平台，整合了订单管理、库存管理、客户服务等功能。',
          icon: 'fas fa-shopping-cart',
          features: [
            '多渠道订单整合',
            '智能库存预警',
            '客户行为分析',
            '营销活动管理'
          ],
          results: [
            { label: '销售增长', value: '35%' },
            { label: '库存周转', value: '50%' },
            { label: '客户留存', value: '70%' }
          ]
        }
      ],
      testimonials: [
        {
          content: '工作室团队非常专业，从需求分析到最终交付，每个环节都做得很到位。开发的系统完全符合我们的业务需求，大大提升了工作效率。',
          author: '张总',
          position: 'CTO',
          company: '某制造企业'
        },
        {
          content: '合作过程中沟通顺畅，技术实力强，能够快速理解我们的需求并提出专业的解决方案。项目按时交付，质量超出预期。',
          author: '李经理',
          position: '产品经理',
          company: '某教育机构'
        },
        {
          content: '系统运行稳定，界面设计美观易用，用户反馈很好。后期的维护服务也很及时，是值得信赖的合作伙伴。',
          author: '王主任',
          position: '信息主任',
          company: '某医院'
        }
      ]
    }
  }
}
</script>

<style scoped>
.studio-cases {
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

.cases-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
  gap: 32px;
  margin-bottom: 80px;
}

.case-card {
  background: #f8fafc;
  border-radius: 16px;
  overflow: hidden;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.case-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
  border-color: #667eea;
}

.case-image {
  height: 200px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.case-placeholder {
  color: white;
  text-align: center;
}

.case-placeholder i {
  font-size: 64px;
}

.case-info {
  padding: 32px;
}

.case-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.case-title {
  font-size: 24px;
  font-weight: 600;
  color: #1a202c;
}

.case-industry {
  padding: 4px 12px;
  background: #667eea;
  color: white;
  border-radius: 50px;
  font-size: 12px;
  font-weight: 500;
}

.case-description {
  color: #4a5568;
  line-height: 1.6;
  margin-bottom: 24px;
}

.case-features {
  margin-bottom: 24px;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
  color: #2d3748;
}

.feature-item i {
  color: #667eea;
  font-size: 12px;
}

.case-results {
  display: flex;
  gap: 24px;
  padding-top: 24px;
  border-top: 1px solid #e2e8f0;
}

.result-item {
  text-align: center;
  flex: 1;
}

.result-value {
  font-size: 24px;
  font-weight: 700;
  color: #667eea;
  margin-bottom: 4px;
}

.result-label {
  font-size: 14px;
  color: #4a5568;
}

.testimonials-section {
  background: #f8fafc;
  border-radius: 16px;
  padding: 48px;
}

.testimonials-title {
  font-size: 32px;
  font-weight: 700;
  color: #1a202c;
  text-align: center;
  margin-bottom: 48px;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 32px;
}

.testimonial-card {
  background: white;
  padding: 32px;
  border-radius: 16px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.07);
  transition: all 0.3s ease;
}

.testimonial-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.testimonial-content {
  margin-bottom: 24px;
}

.quote-icon {
  color: #667eea;
  font-size: 24px;
  margin-bottom: 16px;
}

.testimonial-text {
  color: #4a5568;
  line-height: 1.6;
  font-style: italic;
}

.testimonial-author {
  display: flex;
  align-items: center;
  gap: 16px;
}

.author-avatar {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 20px;
}

.author-name {
  font-size: 16px;
  font-weight: 600;
  color: #1a202c;
  margin-bottom: 4px;
}

.author-position {
  font-size: 14px;
  color: #667eea;
  margin-bottom: 2px;
}

.author-company {
  font-size: 12px;
  color: #4a5568;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .studio-cases {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 32px;
  }
  
  .section-description {
    font-size: 16px;
  }
  
  .cases-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .case-info {
    padding: 24px;
  }
  
  .case-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 8px;
  }
  
  .case-results {
    flex-direction: column;
    gap: 16px;
  }
  
  .testimonials-section {
    padding: 32px 24px;
  }
  
  .testimonials-title {
    font-size: 28px;
  }
  
  .testimonials-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .testimonial-card {
    padding: 24px;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 28px;
  }
  
  .case-title {
    font-size: 20px;
  }
  
  .testimonials-section {
    padding: 24px 16px;
  }
  
  .testimonial-author {
    flex-direction: column;
    text-align: center;
    gap: 12px;
  }
}

/* 深色主题 */
:global(.dark) .studio-cases {
  background: #0f172a;
}

:global(.dark) .section-title {
  color: #f1f5f9;
}

:global(.dark) .section-description {
  color: #cbd5e1;
}

:global(.dark) .case-card {
  background: #1e293b;
}

:global(.dark) .case-title {
  color: #f1f5f9;
}

:global(.dark) .case-description {
  color: #cbd5e1;
}

:global(.dark) .feature-item {
  color: #f1f5f9;
}

:global(.dark) .result-label {
  color: #cbd5e1;
}

:global(.dark) .testimonials-section {
  background: #1e293b;
}

:global(.dark) .testimonials-title {
  color: #f1f5f9;
}

:global(.dark) .testimonial-card {
  background: #334155;
}

:global(.dark) .testimonial-text {
  color: #cbd5e1;
}

:global(.dark) .author-name {
  color: #f1f5f9;
}

:global(.dark) .author-company {
  color: #cbd5e1;
}
</style>
