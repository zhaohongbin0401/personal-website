# 个人网站 技术设计文档（TECH_DESIGN）

> 版本：v1.0　日期：2026-10-27

## 1. 技术选型

| 项目 | 选择 | 理由 |
| --- | --- | --- |
| 语言 | HTML + CSS + 原生 JS | 纯静态站，无构建依赖，部署最简单 |
| 样式 | 手写 CSS（CSS 变量 + Flex/Grid） | 体积小、可完全自定义，满足个性化要求 |
| 图标 | 内联 SVG / Unicode | 零外部请求，离线可用 |
| 托管 | GitHub Pages | 免费、自动分配域名、支持 HTTPS |
| 版本管理 | Git（main 分支） | 课程要求 Git 即时提交 |
| 开发辅助 | Trae（AI 对话式开发） | 文档驱动生成代码 |

## 2. 架构

```
浏览器 ──> GitHub Pages CDN ──> index.html（单文件，无后端）
```

- 无服务端、无数据库、无构建步骤，资源全部内联或同目录引用。

## 3. 目录结构

```
demo10.27/
├── index.html      # 个人网站（唯一页面）
├── PRD.md          # 产品需求文档
├── TECH_DESIGN.md  # 技术设计文档
└── AGENTS.md       # AI 项目说明
```

## 4. 设计规范

- 主色：`#14b8a6`（青绿）　背景：`#0b1120`（深蓝黑）　强调发光：`rgba(20,184,166,.35)`
- 字体：系统字体栈（PingFang SC / Microsoft YaHei + 等宽 fallback）
- 布局：移动优先，`grid-template-columns: repeat(auto-fit, minmax(260px, 1fr))` 自适应卡片
- 动画：CSS transition + 少量 JS IntersectionObserver 做滚动淡入

## 5. AI 开发规范（供 Trae 等 Agent 遵守）

1. 所有修改只作用于 `index.html`，不引入外部库和构建工具；
2. 图片资源优先使用占位 SVG/CSS 图形，不依赖外链图床；
3. 代码注释使用中文，组件命名语义化；
4. 保持单文件结构，除非需求明确要求拆分。

## 6. 部署步骤

```bash
# 本地预览
python -m http.server 8123 --directory D:\Practice\demo10.27

# 上传（由于本机 git push 连 github.com 被重置，改用 REST API）
# 1) 创建仓库 personal-website（Public）
# 2) PUT /repos/zhaohongbin0401/personal-website/contents/{file}
# 3) POST /repos/zhaohongbin0401/personal-website/pages  {source:{branch:"main", path:"/"}}
# 4) 访问 https://zhaohongbin0401.github.io/personal-website/
```

## 7. 风险与对策

| 风险 | 对策 |
| --- | --- |
| GitHub 连接不稳定 | 使用 api.github.com REST 接口上传 |
| 样式被浏览器缓存 | 部署后强制刷新（Ctrl+F5）验证 |
