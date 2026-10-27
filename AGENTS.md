# AGENTS.md — 个人网站项目说明

> 供 AI 编程助手（Trae / Codex / Copilot 等）读取的项目上下文。

## 项目是什么

赵鸿斌（物联网243班，学号 2023173227）的个人网站，纯静态单页应用，用于展示个人信息、技能、项目与联系方式。部署于 GitHub Pages。

## 怎么运行

```bash
# 本地预览
python -m http.server 8123 --directory D:\Practice\demo10.27
# 浏览器打开 http://localhost:8123
```

## 硬性约定

1. **单文件**：所有页面代码只写在一个 `index.html` 中（CSS、JS 内联），不引入任何外部库、CDN 或构建工具；
2. **无外链资源**：图标用内联 SVG，头像用 CSS/SVG 占位，禁止依赖第三方图床；
3. **风格**：深色科技风，主色 `#14b8a6`（青绿），背景 `#0b1120`，保持个性化，不套用常见蓝紫渐变模板；
4. **语言**：界面文案与代码注释使用中文；
5. **兼容**：支持 Chrome / Edge 最新版，移动端 375px 不破版。

## 目录结构

```
demo10.27/
├── index.html      # 个人网站页面（唯一实现文件）
├── PRD.md          # 产品需求文档
├── TECH_DESIGN.md  # 技术设计文档
└── AGENTS.md       # 本文件
```

## 内容数据

- 姓名：赵鸿斌
- 班级 / 学号：物联网243班 / 2023173227
- GitHub：zhaohongbin0401
- 技能：HTML/CSS/JS、Vue3、Spring Boot、MyBatis-Plus、C51、Keil、Trae
- 项目：图片水印助手（zhaohongbin0401.github.io/watermark-tool）、AI 翻译助手（zhaohongbin0401.github.io/ai-translator）、电商图片下载插件

## 修改规则

- 改内容：直接改 `index.html` 中对应区块；
- 改风格：优先修改 CSS 变量区（:root）；
- 改完必须本地预览验证，再提交。
