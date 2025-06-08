<template>
  <div class="modern-home">
    <!-- 现代化英雄区域 -->
    <ModernHero :info="personalInfo" />

    <!-- 关于我区域 -->
    <section id="about" class="section">
      <about/>
    </section>

    <!-- 工作经验区域 -->
    <section id="experience" class="section">
      <experience/>
    </section>

    <!-- 技能展示区域 -->
    <section id="skills" class="section">
      <skill/>
    </section>

    <!-- 项目展示区域 -->
    <section id="projects" class="section">
      <project/>
    </section>

    <!-- 联系方式区域 -->
    <section id="contact" class="section">
      <bottom/>
    </section>
  </div>
</template>

<script>
import ModernHero from '@/components/modern/ModernHero.vue'
import bottom from '@/components/bottom.vue'
import about from '@/components/about.vue'
import experience from '@/components/experience.vue'
import skill from '@/components/skill.vue'
import project from '@/components/project.vue'
export default {
  name: 'ModernHome',
  data () {
    return {
      personalInfo: {
        name: 'Your Name',
        job: 'Full Stack Developer',
        description: '热爱技术，专注于创造优秀的用户体验和高质量的代码。擅长前端开发、后端架构设计，致力于用技术改变世界。',
        experience: '3+',
        projects: '50+',
        clients: '20+',
        birth: '1995-01',
        wechat: '3年',
        address: '北京市',
        website: 'https://your-blog.com'
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
    ModernHero,
  	bottom,
  	about,
  	experience,
  	skill,
  	project
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.modern-home {
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

