# 🌟 个人简历网站

<div align="center">

![Vue.js](https://img.shields.io/badge/Vue.js-2.5.2-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![Webpack](https://img.shields.io/badge/Webpack-3.6.0-8DD6F9?style=for-the-badge&logo=webpack&logoColor=black)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**一个现代化、响应式的个人简历网站模板**

[🚀 在线演示](https://vqlai.github.io/dist/#/) • [📖 文档](#文档) • [🐛 报告问题](https://github.com/vqlai/vqlai.github.io/issues) • [💡 功能请求](https://github.com/vqlai/vqlai.github.io/issues)

</div>

---

## 📋 项目简介

这是一个基于 **Vue.js 2** 开发的现代化个人简历网站模板。项目采用组件化开发模式，具有良好的代码结构和可维护性，非常适合：

- 🎓 **Vue.js 初学者**学习组件化开发
- 💼 **求职者**快速搭建个人简历网站
- 🛠️ **开发者**了解前端工程化实践
- 📚 **学习者**掌握现代前端开发技术栈

## ✨ 主要特性

- 🎨 **现代化设计** - 简洁美观的 UI 界面
- 📱 **响应式布局** - 完美适配各种设备
- ⚡ **高性能** - 优化的构建配置和资源加载
- 🧩 **组件化架构** - 易于维护和扩展
- 🎭 **动画效果** - 流畅的交互体验
- 🔧 **易于定制** - 灵活的配置和样式系统
- 📦 **开箱即用** - 完整的开发和构建环境

## 🛠️ 技术栈

### 核心技术
- **Vue.js 2.5.2** - 渐进式 JavaScript 框架
- **Vue Router 3.0.1** - 官方路由管理器
- **Webpack 3.6.0** - 模块打包工具
- **ES6+** - 现代 JavaScript 语法

### 特色插件
- **vue-particles** - 粒子背景效果
- **vue-awesome-swiper** - 轮播图组件
- **Babel** - JavaScript 编译器
- **PostCSS** - CSS 后处理器

## 🚀 快速开始

### 环境要求

- **Node.js** >= 6.0.0
- **npm** >= 3.0.0

### 安装步骤

1. **克隆项目**
   ```bash
   git clone https://github.com/vqlai/vqlai.github.io.git
   cd vqlai.github.io
   ```

2. **安装依赖**
   ```bash
   npm install
   # 或使用淘宝镜像（推荐）
   npm install --registry=https://registry.npm.taobao.org
   ```

3. **启动开发服务器**
   ```bash
   npm run dev
   ```

4. **访问应用**

   打开浏览器访问 [http://localhost:1008](http://localhost:1008)

### 构建部署

```bash
# 构建生产版本
npm run build

# 构建文件将生成在 dist/ 目录下
```

## 📁 项目结构

```
vqlai.github.io/
├── build/                  # 构建配置文件
├── config/                 # 项目配置文件
├── src/                    # 源代码目录
│   ├── components/         # Vue 组件
│   │   ├── about.vue      # 关于我组件
│   │   ├── bottom.vue     # 底部组件
│   │   ├── experience.vue # 工作经验组件
│   │   ├── project.vue    # 项目展示组件
│   │   ├── skill.vue      # 技能组件
│   │   └── top.vue        # 顶部组件
│   ├── pages/             # 页面组件
│   │   └── home/          # 首页
│   ├── router/            # 路由配置
│   ├── common/            # 公共资源
│   │   ├── css/          # 样式文件
│   │   └── images/       # 图片资源
│   ├── App.vue           # 根组件
│   └── main.js           # 入口文件
├── static/               # 静态资源
├── package.json         # 项目依赖
└── README.md           # 项目说明
```

## 🎨 自定义指南

### 修改个人信息

1. **基本信息**：编辑 `src/components/about.vue`
2. **工作经验**：编辑 `src/components/experience.vue`
3. **技能展示**：编辑 `src/components/skill.vue`
4. **项目展示**：编辑 `src/components/project.vue`

### 更换图片资源

将您的图片放入 `src/common/images/` 目录，然后在对应组件中更新图片路径。

### 自定义样式

每个组件都有独立的样式作用域，您可以直接在组件的 `<style scoped>` 标签中修改样式。

### 添加新功能

1. 在 `src/components/` 目录下创建新组件
2. 在 `src/pages/home/home.vue` 中引入并使用新组件
3. 如需路由，在 `src/router/index.js` 中添加路由配置

## 🌐 浏览器支持

- ✅ Chrome (推荐)
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ❌ IE <= 8

## 🤝 贡献指南

我们欢迎所有形式的贡献！

1. **Fork** 本项目
2. **创建**您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. **提交**您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. **推送**到分支 (`git push origin feature/AmazingFeature`)
5. **打开** Pull Request

## 📝 许可证

本项目基于 [MIT License](LICENSE) 开源协议。

## 💬 交流与支持

- 🐛 **问题反馈**：[提交 Issue](https://github.com/vqlai/vqlai.github.io/issues)
- 💡 **功能建议**：[功能请求](https://github.com/vqlai/vqlai.github.io/issues)
- ⭐ **喜欢项目**：给个 Star 支持一下！

## 📈 更新日志

### v2.0.0 (2018/2/6)
- ✨ 代码优化，新增滚动按钮
- 🎉 完成第二版本开发

### v2.0.0-beta (2018/2/5)
- ✨ 新增项目展示板块
- 🐛 修复 CSS 背景图片路径错误
- 🐛 修复 swiper 无法自动播放问题

### v2.0.0-alpha (2018/2/2)
- 🔨 开始重构代码
- 📝 修改代码结构
- 🗑️ 删除冗余代码

### v1.x 版本历史
<details>
<summary>点击查看 v1.x 版本更新记录</summary>

- **2017/5/14** - 🎨 header 页使用 vue-particles 新增粒子效果
- **2017/3/28** - 🎨 样式调整，代码优化，项目代码全部上传
- **2017/3/26** - ✨ 增加页面预加载和置顶功能，使用 vue-spinner，vue-awesome-swiper 优化交互
- **2017/3/21** - ✨ 新增 footer 联系页面
- **2017/3/17** - 🎨 优化页面 title 样式，修复父子间通信百分比显示错误 bug
- **2017/3/12** - ✨ 增加 skills 页面的父子间通信
- **2017/3/12** - 📱 页面优化，更好的兼容手机端，project 模块的路由
- **2017/2/21** - ✨ 添加了 education 与 experience 页面
- **2017/2/19** - 🔧 添加数据 mock，并且使用 axios 异步加载数据 mock
- **2017/2/19** - ✨ 添加导航，添加 about 模块
- **2017/2/19** - 🎨 首页头部更新
- **2017/2/18** - 📝 更新本项目 README

</details>

---

<div align="center">

**如果这个项目对您有帮助，请给个 ⭐ Star 支持一下！**

Made with ❤️ by [vqlai](https://github.com/vqlai)

</div>