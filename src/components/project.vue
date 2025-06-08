<template>
  <div class="project">
    <div class="container">
      <span class="tip">WHAT I DO</span>
      <h1 class="title">{{title}}</h1>
      <span class="border"></span>
      <ul>
        <li v-for="(project, index) in projects" :key="index" @click="handleProjectClick(project)">
          <img :src="project.image" :alt="project.title">
          <div class="project-overlay">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <span class="click-hint">点击查看详情</span>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'project',
  data () {
    return {
      title: '我的项目',
      projects: [
        {
          title: '应用商店',
          description: '下载你喜欢的应用！',
          image: require('../common/images/project1.jpg'),
          link: 'https://fbxdadsofwvfktbcbbos.supabase.co/storage/v1/object/public/apk//appstore_demo.apk',
          technologies: ['Android', 'Java', 'Firebase']
        },
        {
          title: '博客系统',
          description: '响应式个人博客管理系统',
          image: require('../common/images/project2.jpg'),
          link: 'https://github.com/yourusername/blog-system',
          technologies: ['React', 'Express', 'MySQL']
        },
        {
          title: '任务管理器',
          description: '团队协作任务管理工具',
          image: require('../common/images/project3.jpg'),
          link: 'https://github.com/yourusername/task-manager',
          technologies: ['Angular', 'Spring Boot', 'PostgreSQL']
        },
        {
          title: '数据可视化',
          description: '企业数据分析可视化平台',
          image: require('../common/images/project4.jpg'),
          link: 'https://github.com/yourusername/data-visualization',
          technologies: ['D3.js', 'Python', 'Flask']
        }
      ]
    }
  },
  methods: {
    handleProjectClick(project) {
      // 检测是否为触摸设备
      const isTouchDevice = 'ontouchstart' in window || navigator.maxTouchPoints > 0;

      if (isTouchDevice) {
        // 手机端：显示确认对话框
        const confirmed = confirm(`${project.title}\n${project.description}\n\n是否要打开此项目？`);
        if (confirmed && project.link) {
          window.open(project.link, '_blank');
        }
      } else {
        // 桌面端：直接打开链接
        if (project.link) {
          window.open(project.link, '_blank');
        }
      }
    },

    // 如果需要显示详情模态框，可以添加这个方法
    showProjectDetails(project) {
      alert(`项目: ${project.title}\n描述: ${project.description}\n技术栈: ${project.technologies.join(', ')}\n\n点击确定访问项目链接`);
      if (project.link) {
        window.open(project.link, '_blank');
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .project{height: auto;width: 100%;margin: 0 auto;background-color: #fff;text-align: center;}
  .container{height: auto;max-width: 1200px;margin: 0 auto;padding: 4% 0;}
  .tip{display:inline-block;position:relative;padding:6px 20px;margin:0 auto 10px;font-size: 20px;background:#03a9f4;color: #fff;}
  .tip:after{position:absolute;width: 0;height: 0;left:42%;bottom:-10px;content: '';border-style: solid;border-width: 10px 10px 0 10px;border-color: #03a9f4 transparent;}
  .title{padding: 6px 0 10px;font-family: 'Overlock', cursive;color: #2F2C06;font-size: 36px;}
  .border{display:block;width: 20%;height: 1px;position:relative;margin:0 auto 30px;background: #8C8989;}
  .border:after{position: absolute;top: 0;left: 30%;content: " ";width: 40%;height: 5px;margin-top:-2px;background: #03a9f4;}

  ul{
    width: 100%;
    padding: 4% 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 20px;
  }
  ul li{
    flex: 1;
    min-width: 200px;
    max-width: calc(25% - 15px);
    height: auto;
    box-sizing: border-box;
    transition: transform .25s ease;
    position: relative;
    cursor: pointer;
    overflow: hidden;
    border-radius: 8px;
    margin-bottom: 20px;
  }
  ul li img{
    width: 100%;
    height: 200px;
    object-fit: cover;
    display: block;
    transition: transform .3s ease;
  }
  ul li:hover{
    z-index: 100;
    -webkit-transform: scale(1.05);
    transform: scale(1.05);
    box-shadow: 0 8px 17px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
  }
  ul li:hover img{
    transform: scale(1.1);
  }

  /* 项目覆盖层样式 */
  .project-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(3, 169, 244, 0.9);
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity .3s ease;
    padding: 20px;
    text-align: center;
  }

  ul li:hover .project-overlay {
    opacity: 1;
  }

  .project-overlay h3 {
    font-size: 18px;
    margin: 0 0 10px 0;
    font-weight: bold;
  }

  .project-overlay p {
    font-size: 14px;
    margin: 0 0 15px 0;
    line-height: 1.4;
  }

  .click-hint {
    font-size: 12px;
    background: rgba(255, 255, 255, 0.2);
    padding: 5px 10px;
    border-radius: 15px;
    border: 1px solid rgba(255, 255, 255, 0.3);
  }

  /* 响应式设计 - 平板设备 */
  @media screen and (max-width: 1024px) {
    .container {
      padding: 3% 2%;
    }

    ul li {
      max-width: calc(50% - 10px);
      min-width: 250px;
    }

    .title {
      font-size: 32px;
    }

    .project-overlay h3 {
      font-size: 16px;
    }

    .project-overlay p {
      font-size: 13px;
    }
  }

  /* 响应式设计 - 手机设备 */
  @media screen and (max-width: 768px) {
    .container {
      padding: 2% 4%;
    }

    .title {
      font-size: 28px;
      text-align: center;
    }

    ul {
      flex-direction: column;
      gap: 15px;
      padding: 2% 0;
    }

    ul li {
      max-width: 100%;
      min-width: 100%;
      margin-bottom: 15px;
    }

    ul li img {
      height: 180px;
    }

    /* 手机端使用点击而非悬停 */
    ul li:active {
      transform: scale(1.02);
    }

    ul li:hover {
      transform: none;
    }

    /* 手机端默认显示项目信息 */
    .project-overlay {
      opacity: 0.8;
      background: rgba(3, 169, 244, 0.85);
      padding: 15px;
    }

    .project-overlay h3 {
      font-size: 16px;
      margin-bottom: 8px;
    }

    .project-overlay p {
      font-size: 12px;
      margin-bottom: 10px;
    }

    .click-hint {
      font-size: 11px;
      padding: 4px 8px;
    }
  }

  /* 响应式设计 - 小屏手机 */
  @media screen and (max-width: 480px) {
    .container {
      padding: 2% 3%;
    }

    .title {
      font-size: 24px;
    }

    .tip {
      font-size: 16px;
      padding: 4px 15px;
    }

    ul li img {
      height: 160px;
    }

    .project-overlay {
      padding: 12px;
    }

    .project-overlay h3 {
      font-size: 14px;
      margin-bottom: 6px;
    }

    .project-overlay p {
      font-size: 11px;
      margin-bottom: 8px;
      line-height: 1.3;
    }

    .click-hint {
      font-size: 10px;
      padding: 3px 6px;
    }
  }

  /* 超小屏设备优化 */
  @media screen and (max-width: 360px) {
    .container {
      padding: 1% 2%;
    }

    .title {
      font-size: 22px;
    }

    ul {
      gap: 12px;
    }

    ul li {
      margin-bottom: 12px;
    }

    ul li img {
      height: 140px;
    }

    .project-overlay {
      padding: 10px;
    }

    .project-overlay h3 {
      font-size: 13px;
      margin-bottom: 5px;
    }

    .project-overlay p {
      font-size: 10px;
      margin-bottom: 6px;
    }
  }
</style>
