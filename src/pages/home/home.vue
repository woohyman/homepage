<template>
  <div class="studio-home">
    <!-- 工作室英雄区域 -->
    <StudioHero :info="studioInfo" />

    <!-- 关于工作室区域 -->
    <section id="about" class="section">
      <StudioAbout/>
    </section>

    <!-- 服务介绍区域 -->
    <section id="services" class="section">
      <StudioServices/>
    </section>

    <!-- 产品展示区域 -->
    <section id="products" class="section">
      <StudioProducts/>
    </section>

    <!-- 客户案例区域 -->
    <section id="cases" class="section">
      <StudioCases/>
    </section>

    <!-- 联系我们区域 -->
    <section id="contact" class="section">
      <StudioContact/>
    </section>
  </div>
</template>

<script>
import StudioHero from '@/components/studio/StudioHero.vue'
import StudioAbout from '@/components/studio/StudioAbout.vue'
import StudioServices from '@/components/studio/StudioServices.vue'
import StudioProducts from '@/components/studio/StudioProducts.vue'
import StudioCases from '@/components/studio/StudioCases.vue'
import StudioContact from '@/components/studio/StudioContact.vue'

export default {
  name: 'StudioHome',
  data () {
    return {
      studioInfo: {
        name: '创新设计工作室',
        slogan: '专业客户端设计与开发',
        description: '专注于客户端软件设计与开发，提供从UI/UX设计到完整应用开发的一站式服务。我们致力于创造优秀的用户体验和高质量的软件产品。',
        founded: '2020',
        projects: '100+',
        clients: '50+',
        downloads: '10万+',
        specialties: ['桌面应用开发', 'UI/UX设计', '跨平台解决方案', '软件架构设计'],
        location: '北京市',
        email: 'studio@example.com',
        phone: '+86 138-0000-0000'
      }
    }
  },
  mounted() {
    this.setupScrollAnimation();
  },
  methods: {
    setupScrollAnimation() {
      // 简化的滚动动画
      const options = {
        threshold: 0.1,
        rootMargin: '0px'
      };

      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('animate-in');
          }
        });
      }, options);

      // 观察所有section
      this.$nextTick(() => {
        const sections = document.querySelectorAll('.section');
        sections.forEach(section => observer.observe(section));
      });
    }
  },
  components:{
    StudioHero,
    StudioAbout,
    StudioServices,
    StudioProducts,
    StudioCases,
    StudioContact
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.studio-home {
  width: 100%;
  min-height: 100vh;
  overflow-x: hidden;
}

.section {
  position: relative;
  width: 100%;
  min-height: auto;
  display: block;
  padding: 0;
}

/* 移除背景样式，让组件自己控制背景 */

/* 确保section正常显示 */
.section {
  opacity: 1;
  visibility: visible;
}

/* 响应式优化 */
@media (max-width: 768px) {
  .modern-home {
    padding: 0;
  }
}
</style>

