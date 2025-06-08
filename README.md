# 🎨 创新设计工作室官网

<div align="center">

![Vue.js](https://img.shields.io/badge/Vue.js-2.5.2-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![Webpack](https://img.shields.io/badge/Webpack-3.6.0-8DD6F9?style=for-the-badge&logo=webpack&logoColor=black)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**专业的客户端设计与软件开发工作室网站**

[🚀 在线演示](#) • [📱 软件下载](#产品展示) • [💼 服务咨询](#联系我们) • [🏆 客户案例](#客户案例)

</div>

---

## 📋 项目简介

这是一个专业的工作室展示网站，专注于客户端软件设计、开发和产品展示。网站采用现代化设计理念，提供完整的商业服务展示和软件下载功能，非常适合：

- 🎨 **设计工作室**展示专业能力和服务
- 💻 **软件开发团队**推广产品和获取客户
- 📱 **应用开发者**提供软件下载和展示
- 🏢 **技术服务商**建立专业品牌形象
- 💼 **自由职业者**转型工作室业务模式

## ✨ 核心功能

### 🎯 商业功能
- 📱 **软件下载** - 一键下载APK等软件文件，无需跳转
- 🎨 **产品展示** - 精美的软件产品展示，支持分类筛选
- 💼 **服务介绍** - 详细的开发服务说明和透明定价
- 🏆 **客户案例** - 成功项目案例和客户评价展示
- 📞 **项目咨询** - 便捷的在线咨询表单和联系方式
- 🏢 **工作室介绍** - 专业团队展示和核心优势

### 🎨 设计特色
- 🌈 **现代化UI** - 采用2024年最新设计趋势
- 🎭 **玻璃态效果** - 毛玻璃质感的界面元素
- ✨ **渐变主题** - 优雅的紫蓝色渐变背景
- 🎪 **流畅动画** - 丰富的交互动画和过渡效果
- 📱 **响应式设计** - 完美适配桌面、平板、手机
- ⚡ **性能优化** - 快速加载和流畅用户体验

## 🛠️ 技术架构

### 前端技术栈
- **Vue.js 2.5.2** - 渐进式 JavaScript 框架
- **Vue Router 3.0.1** - 单页应用路由管理
- **Webpack 3.6.0** - 模块打包和构建工具
- **ES6+** - 现代 JavaScript 语法特性

### 工作室组件
- **StudioHero** - 工作室英雄区域展示
- **StudioAbout** - 团队介绍和核心优势
- **StudioServices** - 服务介绍和定价体系
- **StudioProducts** - 产品展示和下载功能
- **StudioCases** - 客户案例和成功故事
- **StudioContact** - 项目咨询和联系方式

### 特色功能
- **vue-particles** - 动态粒子背景效果
- **软件下载系统** - 支持APK等文件直接下载
- **产品筛选** - 按平台分类展示产品
- **响应式布局** - 移动端优先的设计理念

## 🚀 快速开始

### 环境要求

- **Node.js** >= 12.0.0
- **npm** >= 6.0.0

### 安装步骤

1. **克隆项目**
   ```bash
   git clone <your-repository-url>
   cd studio-website
   ```

2. **安装依赖**
   ```bash
   npm install
   ```

3. **启动开发服务器**
   ```bash
   npm run dev
   ```

4. **访问工作室网站**

   打开浏览器访问 [http://localhost:1008](http://localhost:1008)

### 构建部署

```bash
# 构建生产版本
npm run build

# 构建文件将生成在 dist/ 目录下
# 可以部署到任何静态网站托管服务
```

### 部署建议

推荐部署平台：
- **GitHub Pages** - 免费静态网站托管
- **Netlify** - 自动部署和CDN加速
- **Vercel** - 快速部署和全球CDN
- **阿里云OSS** - 国内访问速度快

## 📁 项目结构

```
studio-website/
├── build/                  # 构建配置文件
├── config/                 # 项目配置文件
├── src/                    # 源代码目录
│   ├── components/         # Vue 组件
│   │   ├── studio/        # 工作室专用组件
│   │   │   ├── StudioHero.vue      # 工作室英雄区域
│   │   │   ├── StudioAbout.vue     # 关于工作室
│   │   │   ├── StudioServices.vue  # 服务介绍
│   │   │   ├── StudioProducts.vue  # 产品展示 (核心)
│   │   │   ├── StudioCases.vue     # 客户案例
│   │   │   └── StudioContact.vue   # 联系合作
│   │   └── modern/        # 现代化组件
│   │       └── ModernNav.vue       # 导航栏
│   ├── pages/             # 页面组件
│   │   └── home/          # 工作室主页
│   ├── router/            # 路由配置
│   ├── styles/            # 样式系统
│   │   ├── modern-design.css       # 现代化设计
│   │   └── performance.css         # 性能优化
│   ├── common/            # 公共资源
│   │   ├── css/          # 样式文件
│   │   └── images/       # 图片资源
│   ├── App.vue           # 根组件
│   └── main.js           # 入口文件
├── static/               # 静态资源
├── package.json         # 项目依赖
└── README.md           # 项目说明
```

## 🎨 自定义配置

### 工作室信息配置

编辑 `src/pages/home/home.vue` 文件中的工作室信息：

```javascript
studioInfo: {
  name: '您的工作室名称',
  slogan: '专业标语',
  description: '工作室介绍',
  founded: '成立年份',
  projects: '项目数量',
  clients: '客户数量',
  downloads: '下载量'
}
```

### 产品展示配置

在 `src/components/studio/StudioProducts.vue` 中添加您的软件产品：

```javascript
products: [
  {
    title: '软件名称',
    description: '软件描述',
    platform: '支持平台',
    category: 'desktop', // desktop/mobile/web
    downloadUrl: '下载链接', // 支持APK直接下载
    features: ['功能1', '功能2'],
    downloads: '下载量',
    rating: '评分'
  }
]
```

### 服务定价配置

在 `src/components/studio/StudioServices.vue` 中配置服务和价格：

```javascript
services: [
  {
    title: '服务名称',
    description: '服务描述',
    features: ['特性1', '特性2'],
    price: '起价'
  }
]
```

### 联系方式配置

在 `src/components/studio/StudioContact.vue` 中更新联系信息：

```javascript
// 更新邮箱、电话、微信、地址等信息
```

## 📱 主要功能

### 🎯 软件下载功能
- **直接下载**: 点击即可下载APK等软件文件
- **无需跳转**: 不需要外部链接或确认弹窗
- **智能提示**: 友好的下载状态反馈
- **多格式支持**: 支持APK、EXE、DMG等格式

### 🎨 产品展示系统
- **智能筛选**: 按平台分类（桌面/移动/Web应用）
- **产品详情**: 完整的功能介绍和技术规格
- **用户数据**: 下载量、评分、更新时间展示
- **响应式卡片**: 现代化的产品展示界面

### 💼 商业服务展示
- **服务定价**: 明确的价格体系和服务内容
- **客户案例**: 成功项目案例和客户评价
- **合作流程**: 完整的项目合作流程展示
- **多种联系方式**: 邮箱、电话、微信等联系方式

## 🌐 浏览器支持

- ✅ Chrome 60+ (推荐)
- ✅ Firefox 55+
- ✅ Safari 12+
- ✅ Edge 79+
- ❌ Internet Explorer

## 🚀 部署指南

### 静态网站托管
推荐使用以下平台部署：

1. **GitHub Pages** - 免费，适合开源项目
2. **Netlify** - 自动部署，CDN加速
3. **Vercel** - 快速部署，全球CDN
4. **阿里云OSS** - 国内访问速度快

### 域名配置
1. 购买域名
2. 配置DNS解析
3. 设置HTTPS证书
4. 配置CDN加速

## 📝 许可证

本项目基于 [MIT License](LICENSE) 开源协议。

## 🎯 使用场景

### 适用对象
- 🎨 **设计工作室** - 展示设计能力和作品集
- 💻 **软件开发团队** - 推广产品和获取客户
- 📱 **应用开发者** - 提供软件下载和展示
- 🏢 **技术服务商** - 建立专业品牌形象
- 💼 **自由职业者** - 转型工作室业务模式

### 商业价值
- ✅ **专业形象展示** - 突出工作室品牌和实力
- ✅ **产品直接推广** - 用户可以直接下载体验
- ✅ **客户获取渠道** - 通过案例和服务吸引客户
- ✅ **商业转化工具** - 从展示到实际业务转化
- ✅ **品牌价值提升** - 专业网站提升品牌形象

## 💬 技术支持

- 📧 **邮箱咨询**: studio@example.com
- 🐛 **问题反馈**: GitHub Issues
- 💡 **功能建议**: GitHub Discussions
- 📱 **微信咨询**: studio_design

## 📈 更新日志

### v3.0.0 (2024/01/01) - 工作室版本
- 🎨 **全新设计** - 从个人简历网站改造为工作室网站
- 📱 **软件下载** - 新增APK等软件文件直接下载功能
- 🏢 **商业展示** - 新增服务介绍、客户案例、项目咨询
- 🎯 **产品展示** - 专业的软件产品展示和筛选系统
- ✨ **现代化UI** - 采用玻璃态设计和渐变主题
- 📱 **响应式优化** - 完美适配所有设备尺寸

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

**🎨 专业工作室网站，助力您的业务发展！**

**⭐ 如果这个项目对您有帮助，请给它一个 Star！**

Made with ❤️ for Creative Studios

</div>