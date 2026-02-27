# Elux Store Frontend - 生产构建

> Premium B2B & B2C E-commerce Platform（优质 B2B 和 B2C 电商平台）

## 📦 项目概述

这是 **Elux Store** 前端应用的生产环境打包版本，采用 Vue 3 + Vite 构建，专为企业零售和电子商务场景设计。

## 🚀 部署说明

### 环境要求

- **Web 服务器**: Nginx / Apache / Caddy 或任何静态文件服务器
- **Node.js**: 无需（已预编译为静态资源）

### 部署步骤

1. **上传文件**: 将 `dist` 目录下的所有文件上传至 Web 服务器根目录

2. **配置服务器**: 确保服务器配置支持：
   - 静态文件服务
   - HTML5 History 模式（SPA 路由）
   - Gzip/Brotli 压缩（可选，推荐）

3. **Nginx 配置示例**:
   ```nginx
   server {
       listen 80;
       server_name your-domain.com;
       root /path/to/dist;
       index index.html;

       # 支持 SPA 路由
       location / {
           try_files $uri $uri/ /index.html;
       }

       # 启用压缩
       gzip on;
       gzip_types text/plain text/css application/json application/javascript text/xml application/xml;
   }
   ```

## 📁 目录结构

```
dist/
├── index.html          # 入口 HTML 文件
├── logo_black.svg      # 黑色 Logo（浅色模式）
├── logo_white.svg      # 白色 Logo（深色模式）
├── grid.svg            # 网格背景图（浅色模式）
├── grid-dark.svg       # 网格背景图（深色模式）
├── assets/             # 编译后的 JS/CSS 资源
│   ├── index-*.js      # 主应用入口
│   ├── index-*.css     # 主样式文件
│   └── ...             # 按需加载的页面组件
├── media/              # 媒体资源
│   ├── brand.jpg       # 品牌图片
│   ├── full_page.jpg   # 全屏背景图
│   ├── logistics.jpg   # 物流相关图片
│   ├── return.png      # 退货相关图片
│   ├── service.png     # 服务相关图片
│   ├── *.mp4           # 3D 展示视频
│   └── *.png           # 产品图片
└── .nojekyll           # 禁用 GitHub Pages Jekyll 处理
```

## 🛍️ 功能模块

### 用户端功能
- **首页浏览** - 企业/个人双模式首页
- **商品展示** - 商品列表与详情页
- **购物车** - 购物车管理
- **订单管理** - 订单列表与详情
- **退货申请** - 退货流程处理
- **用户中心** - 个人资料与地址管理

### 企业功能
- **企业注册** - 企业用户注册
- **批量订购** - B2B 批量采购
- **企业主页** - 企业专属展示页

### 其他功能
- **登录/注册** - 用户认证
- **密码找回** - 忘记密码功能
- **结账流程** - 完整的购物结账流程

## 🔧 技术栈

- **框架**: Vue 3
- **构建工具**: Vite
- **路由**: Vue Router
- **UI 组件**: 自定义组件 + Lucide 图标
- **动画**: ScrollTrigger

## 📝 注意事项

1. **路径配置**: 如果部署在非根路径，需要修改 `vite.config.js` 中的 `base` 配置并重新构建

2. **API 地址**: 确保后端 API 地址配置正确（通常在 `.env` 文件中配置）

3. **缓存策略**: 建议为 `assets` 目录配置长期缓存（带哈希的文件名支持）

4. **CORS**: 如果前后端分离部署，确保后端配置了正确的 CORS 策略

## 📄 许可证

本项目为商业软件，未经授权不得用于商业用途。

---

**构建时间**: 2026 年 2 月  
**版本**: Production Build
