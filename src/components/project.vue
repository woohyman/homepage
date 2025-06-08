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
        <div class="clearfix"></div>
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
      // 可以选择以下几种方式之一：

      // 方式1: 直接在新窗口打开项目链接
      if (project.link) {
        window.open(project.link, '_blank');
      }

      // 方式2: 显示项目详情（可以取消注释使用）
      // this.showProjectDetails(project);

      // 方式3: 触发自定义事件（如果需要父组件处理）
      // this.$emit('project-clicked', project);
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

  ul{width: 100%;padding: 4% 0;}
  ul li{
    float: left;
    width: 20%;
    margin-right: 5%;
    height: 80%;
    box-sizing: border-box;
    transition: transform .25s ease;
    position: relative;
    cursor: pointer;
    overflow: hidden;
    border-radius: 8px;
  }
  ul li img{width: 100%;display: block;transition: transform .3s ease;}
  ul li:hover{
    z-index: 100;
    -webkit-transform: scale(1.1);
    transform: scale(1.2);
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
</style>
