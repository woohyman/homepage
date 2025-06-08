<template>
  <div class="studio-products">
    <div class="container">
      <!-- 标题区域 -->
      <div class="section-header">
        <div class="section-badge">
          <span class="badge-icon">📱</span>
          <span>产品展示</span>
        </div>
        <h2 class="section-title">精品软件作品</h2>
        <p class="section-description">
          展示我们开发的优质客户端软件，涵盖桌面应用、移动应用等多个平台
        </p>
      </div>
      
      <!-- 产品筛选 -->
      <div class="products-filter">
        <button 
          class="filter-btn" 
          :class="{ active: activeFilter === 'all' }"
          @click="setFilter('all')"
        >
          全部产品
        </button>
        <button 
          class="filter-btn" 
          :class="{ active: activeFilter === 'desktop' }"
          @click="setFilter('desktop')"
        >
          桌面应用
        </button>
        <button 
          class="filter-btn" 
          :class="{ active: activeFilter === 'mobile' }"
          @click="setFilter('mobile')"
        >
          移动应用
        </button>
        <button 
          class="filter-btn" 
          :class="{ active: activeFilter === 'web' }"
          @click="setFilter('web')"
        >
          Web应用
        </button>
      </div>
      
      <!-- 产品网格 -->
      <div class="products-grid">
        <div 
          v-for="product in filteredProducts" 
          :key="product.id"
          class="product-card"
          @click="showProductDetail(product)"
        >
          <div class="product-image">
            <div class="product-placeholder">
              <i :class="product.icon"></i>
              <div class="product-overlay">
                <div class="overlay-content">
                  <button class="download-btn" @click.stop="downloadProduct(product)">
                    <i class="fas fa-download"></i>
                    <span>{{ product.downloadText }}</span>
                  </button>
                </div>
              </div>
            </div>
          </div>
          
          <div class="product-info">
            <div class="product-header">
              <h3 class="product-title">{{ product.title }}</h3>
              <span class="product-platform">{{ product.platform }}</span>
            </div>
            
            <p class="product-description">{{ product.description }}</p>
            
            <div class="product-features">
              <span 
                v-for="feature in product.features" 
                :key="feature"
                class="feature-tag"
              >
                {{ feature }}
              </span>
            </div>
            
            <div class="product-stats">
              <div class="stat-item">
                <i class="fas fa-download"></i>
                <span>{{ product.downloads }}</span>
              </div>
              <div class="stat-item">
                <i class="fas fa-star"></i>
                <span>{{ product.rating }}</span>
              </div>
              <div class="stat-item">
                <i class="fas fa-calendar"></i>
                <span>{{ product.lastUpdate }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 产品详情模态框 -->
    <div v-if="showModal" class="product-modal" @click="closeModal">
      <div class="modal-content" @click.stop>
        <div class="modal-header">
          <h2>{{ selectedProduct.title }}</h2>
          <button class="modal-close" @click="closeModal">
            <i class="fas fa-times"></i>
          </button>
        </div>
        
        <div class="modal-body">
          <div class="product-detail-image">
            <i :class="selectedProduct.icon"></i>
          </div>
          
          <div class="product-detail-info">
            <p class="product-detail-description">{{ selectedProduct.detailDescription }}</p>
            
            <div class="product-detail-meta">
              <div class="meta-item">
                <strong>平台：</strong> {{ selectedProduct.platform }}
              </div>
              <div class="meta-item">
                <strong>版本：</strong> {{ selectedProduct.version }}
              </div>
              <div class="meta-item">
                <strong>大小：</strong> {{ selectedProduct.size }}
              </div>
              <div class="meta-item">
                <strong>更新时间：</strong> {{ selectedProduct.lastUpdate }}
              </div>
            </div>
            
            <div class="product-detail-features">
              <h4>主要功能：</h4>
              <ul>
                <li v-for="feature in selectedProduct.detailFeatures" :key="feature">{{ feature }}</li>
              </ul>
            </div>
          </div>
        </div>
        
        <div class="modal-footer">
          <button class="btn btn-outline" @click="closeModal">关闭</button>
          <button class="btn btn-primary" @click="downloadProduct(selectedProduct)">
            <i class="fas fa-download"></i>
            <span>{{ selectedProduct.downloadText }}</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudioProducts',
  data() {
    return {
      activeFilter: 'all',
      showModal: false,
      selectedProduct: null,
      products: [
        {
          id: 1,
          title: '智能应用商店',
          description: '功能完整的Android应用商店，支持应用下载、更新管理、用户评价等功能。',
          detailDescription: '这是一个功能完整的Android应用商店，采用Material Design设计理念，提供流畅的用户体验。支持应用的浏览、搜索、下载、安装、更新等完整功能，同时具备用户评价、应用推荐等社交功能。',
          platform: 'Android',
          category: 'mobile',
          features: ['应用管理', '自动更新', '用户评价', '安全检测'],
          detailFeatures: [
            '应用浏览和搜索功能',
            '一键下载和安装',
            '自动更新检测',
            '用户评价和评分系统',
            '应用安全扫描',
            '个性化推荐',
            'Material Design界面'
          ],
          downloads: '5000+',
          rating: '4.8',
          lastUpdate: '2024-01',
          version: 'v2.1.0',
          size: '15.2MB',
          icon: 'fab fa-google-play',
          downloadUrl: 'https://fbxdadsofwvfktbcbbos.supabase.co/storage/v1/object/public/apk//appstore_demo.apk',
          downloadText: '立即下载'
        },
        {
          id: 2,
          title: '设计工具箱',
          description: '专业的UI/UX设计工具，支持原型设计、界面设计、图标制作等功能。',
          detailDescription: '一款专为设计师打造的桌面设计工具，集成了原型设计、界面设计、图标制作等多种功能。支持多种设计格式导出，内置丰富的设计素材库，提供团队协作功能。',
          platform: 'Windows/macOS',
          category: 'desktop',
          features: ['原型设计', '界面设计', '图标制作', '团队协作'],
          detailFeatures: [
            '拖拽式界面设计',
            '丰富的组件库',
            '实时预览功能',
            '多格式导出',
            '版本控制',
            '团队协作',
            '插件扩展'
          ],
          downloads: '3000+',
          rating: '4.9',
          lastUpdate: '2024-01',
          version: 'v1.5.2',
          size: '125MB',
          icon: 'fas fa-paint-brush',
          downloadUrl: '#',
          downloadText: '即将发布'
        },
        {
          id: 3,
          title: '项目管理助手',
          description: '高效的项目管理工具，支持任务分配、进度跟踪、团队协作等功能。',
          detailDescription: '一款专业的项目管理工具，帮助团队高效协作。支持项目创建、任务分配、进度跟踪、文件共享等功能，提供多种视图模式，适合各种规模的团队使用。',
          platform: 'Web应用',
          category: 'web',
          features: ['任务管理', '进度跟踪', '团队协作', '文件共享'],
          detailFeatures: [
            '项目看板视图',
            '甘特图进度管理',
            '任务分配和跟踪',
            '团队沟通工具',
            '文件版本管理',
            '时间统计',
            '报表生成'
          ],
          downloads: '8000+',
          rating: '4.7',
          lastUpdate: '2024-01',
          version: 'v3.2.1',
          size: 'Web应用',
          icon: 'fas fa-tasks',
          downloadUrl: '#',
          downloadText: '在线使用'
        },
        {
          id: 4,
          title: '代码编辑器',
          description: '轻量级代码编辑器，支持多种编程语言，具备智能提示、语法高亮等功能。',
          detailDescription: '一款轻量级但功能强大的代码编辑器，支持多种编程语言的语法高亮、智能提示、代码折叠等功能。内置终端、文件管理器，支持插件扩展。',
          platform: 'Windows/macOS/Linux',
          category: 'desktop',
          features: ['语法高亮', '智能提示', '插件支持', '多标签'],
          detailFeatures: [
            '多语言支持',
            '智能代码补全',
            '语法错误检测',
            '代码格式化',
            '集成终端',
            '文件管理器',
            '主题定制'
          ],
          downloads: '12000+',
          rating: '4.6',
          lastUpdate: '2024-01',
          version: 'v2.8.0',
          size: '85MB',
          icon: 'fas fa-code',
          downloadUrl: '#',
          downloadText: '即将发布'
        },
        {
          id: 5,
          title: '图片处理工具',
          description: '简单易用的图片处理工具，支持裁剪、滤镜、格式转换等功能。',
          detailDescription: '一款简单易用的图片处理工具，提供图片裁剪、旋转、滤镜、格式转换等基础功能。界面简洁直观，支持批量处理，适合日常图片处理需求。',
          platform: 'iOS/Android',
          category: 'mobile',
          features: ['图片裁剪', '滤镜效果', '格式转换', '批量处理'],
          detailFeatures: [
            '多种裁剪比例',
            '丰富的滤镜效果',
            '亮度对比度调节',
            '多格式支持',
            '批量处理',
            '云端同步',
            '分享功能'
          ],
          downloads: '25000+',
          rating: '4.5',
          lastUpdate: '2024-01',
          version: 'v1.3.5',
          size: '28MB',
          icon: 'fas fa-image',
          downloadUrl: '#',
          downloadText: '即将发布'
        },
        {
          id: 6,
          title: '数据分析平台',
          description: '强大的数据分析和可视化平台，支持多种数据源和图表类型。',
          detailDescription: '一个功能强大的数据分析和可视化平台，支持连接多种数据源，提供丰富的图表类型和分析工具。具备实时数据处理能力，支持自定义仪表板。',
          platform: 'Web应用',
          category: 'web',
          features: ['数据连接', '可视化图表', '实时分析', '自定义仪表板'],
          detailFeatures: [
            '多数据源连接',
            '拖拽式图表创建',
            '实时数据更新',
            '交互式仪表板',
            '数据导出',
            '权限管理',
            'API接口'
          ],
          downloads: '6000+',
          rating: '4.8',
          lastUpdate: '2024-01',
          version: 'v2.0.3',
          size: 'Web应用',
          icon: 'fas fa-chart-bar',
          downloadUrl: '#',
          downloadText: '在线试用'
        }
      ]
    }
  },
  computed: {
    filteredProducts() {
      if (this.activeFilter === 'all') {
        return this.products;
      }
      return this.products.filter(product => product.category === this.activeFilter);
    }
  },
  methods: {
    setFilter(filter) {
      this.activeFilter = filter;
    },
    showProductDetail(product) {
      this.selectedProduct = product;
      this.showModal = true;
      document.body.style.overflow = 'hidden';
    },
    closeModal() {
      this.showModal = false;
      this.selectedProduct = null;
      document.body.style.overflow = '';
    },
    downloadProduct(product) {
      if (product.downloadUrl && product.downloadUrl !== '#') {
        // 如果是APK文件，直接下载
        if (product.downloadUrl.endsWith('.apk')) {
          const link = document.createElement('a');
          link.href = product.downloadUrl;
          link.download = `${product.title.replace(/\s+/g, '_')}.apk`;
          link.style.display = 'none';
          document.body.appendChild(link);
          link.click();
          document.body.removeChild(link);
          
          alert(`${product.title} 开始下载！`);
        } else {
          window.open(product.downloadUrl, '_blank');
        }
      } else {
        alert(`${product.title} 即将发布，敬请期待！`);
      }
    }
  }
}
</script>

<style scoped>
.studio-products {
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

.products-filter {
  display: flex;
  justify-content: center;
  gap: 16px;
  margin-bottom: 48px;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 12px 24px;
  background: white;
  border: 2px solid #e2e8f0;
  border-radius: 50px;
  color: #4a5568;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-btn:hover,
.filter-btn.active {
  background: #667eea;
  border-color: #667eea;
  color: white;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 32px;
}

.product-card {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.07);
  transition: all 0.3s ease;
  cursor: pointer;
}

.product-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
}

.product-image {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.product-placeholder {
  color: white;
  text-align: center;
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-placeholder i {
  font-size: 64px;
}

.product-overlay {
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
  transition: opacity 0.3s ease;
}

.product-card:hover .product-overlay {
  opacity: 1;
}

.download-btn {
  background: white;
  color: #667eea;
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 8px;
}

.download-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
}

.product-info {
  padding: 24px;
}

.product-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.product-title {
  font-size: 20px;
  font-weight: 600;
  color: #1a202c;
}

.product-platform {
  padding: 4px 12px;
  background: #667eea;
  color: white;
  border-radius: 50px;
  font-size: 12px;
  font-weight: 500;
}

.product-description {
  color: #4a5568;
  line-height: 1.6;
  margin-bottom: 16px;
}

.product-features {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 16px;
}

.feature-tag {
  padding: 4px 8px;
  background: #f7fafc;
  color: #4a5568;
  border-radius: 4px;
  font-size: 12px;
  font-weight: 500;
}

.product-stats {
  display: flex;
  gap: 16px;
  padding-top: 16px;
  border-top: 1px solid #e2e8f0;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 4px;
  color: #4a5568;
  font-size: 14px;
}

.stat-item i {
  color: #667eea;
}

/* 模态框样式 */
.product-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 20px;
}

.modal-content {
  background: white;
  border-radius: 16px;
  max-width: 600px;
  width: 100%;
  max-height: 80vh;
  overflow-y: auto;
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
}

.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 24px;
  border-bottom: 1px solid #e2e8f0;
}

.modal-header h2 {
  font-size: 24px;
  font-weight: 600;
  color: #1a202c;
}

.modal-close {
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #4a5568;
  transition: color 0.3s ease;
}

.modal-close:hover {
  color: #1a202c;
}

.modal-body {
  padding: 24px;
}

.product-detail-image {
  text-align: center;
  margin-bottom: 24px;
}

.product-detail-image i {
  font-size: 80px;
  color: #667eea;
}

.product-detail-description {
  font-size: 16px;
  line-height: 1.6;
  color: #4a5568;
  margin-bottom: 24px;
}

.product-detail-meta {
  margin-bottom: 24px;
}

.meta-item {
  margin-bottom: 8px;
  color: #1a202c;
}

.product-detail-features h4 {
  margin-bottom: 12px;
  color: #1a202c;
}

.product-detail-features ul {
  list-style: none;
  padding: 0;
}

.product-detail-features li {
  padding: 8px 0;
  color: #4a5568;
  position: relative;
  padding-left: 24px;
}

.product-detail-features li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #667eea;
  font-weight: bold;
}

.modal-footer {
  display: flex;
  gap: 12px;
  justify-content: flex-end;
  padding: 24px;
  border-top: 1px solid #e2e8f0;
}

.btn {
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 8px;
}

.btn-outline {
  background: white;
  color: #4a5568;
  border: 2px solid #e2e8f0;
}

.btn-outline:hover {
  background: #f7fafc;
}

.btn-primary {
  background: #667eea;
  color: white;
}

.btn-primary:hover {
  background: #5a67d8;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .studio-products {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 32px;
  }
  
  .section-description {
    font-size: 16px;
  }
  
  .products-filter {
    gap: 8px;
  }
  
  .filter-btn {
    padding: 8px 16px;
    font-size: 14px;
  }
  
  .products-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .product-info {
    padding: 20px;
  }
  
  .modal-content {
    margin: 20px;
    max-height: 90vh;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 28px;
  }
  
  .product-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 8px;
  }
  
  .product-stats {
    flex-direction: column;
    gap: 8px;
  }
  
  .modal-footer {
    flex-direction: column;
  }
}

/* 深色主题 */
:global(.dark) .studio-products {
  background: #0f172a;
}

:global(.dark) .section-title {
  color: #f1f5f9;
}

:global(.dark) .section-description {
  color: #cbd5e1;
}

:global(.dark) .filter-btn {
  background: #1e293b;
  border-color: #334155;
  color: #cbd5e1;
}

:global(.dark) .filter-btn:hover,
:global(.dark) .filter-btn.active {
  background: #667eea;
  border-color: #667eea;
  color: white;
}

:global(.dark) .product-card {
  background: #1e293b;
}

:global(.dark) .product-title {
  color: #f1f5f9;
}

:global(.dark) .product-description {
  color: #cbd5e1;
}

:global(.dark) .feature-tag {
  background: #334155;
  color: #cbd5e1;
}

:global(.dark) .stat-item {
  color: #cbd5e1;
}

:global(.dark) .modal-content {
  background: #1e293b;
}

:global(.dark) .modal-header h2 {
  color: #f1f5f9;
}

:global(.dark) .modal-close {
  color: #cbd5e1;
}

:global(.dark) .modal-close:hover {
  color: #f1f5f9;
}

:global(.dark) .product-detail-description {
  color: #cbd5e1;
}

:global(.dark) .meta-item {
  color: #f1f5f9;
}

:global(.dark) .product-detail-features h4 {
  color: #f1f5f9;
}

:global(.dark) .product-detail-features li {
  color: #cbd5e1;
}

:global(.dark) .btn-outline {
  background: #334155;
  color: #cbd5e1;
  border-color: #475569;
}

:global(.dark) .btn-outline:hover {
  background: #475569;
}
</style>
