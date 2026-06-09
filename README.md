# School-Score-Counter# 🎓 学分规划器 (Credit Planner)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

一款专为大学生设计的纯本地化学分与课业进度管理工具。通过可视化的看板和甘特图，帮助你轻松追踪毕业学分要求、各学期课业压力，并支持一键计算挂科重修状态。

> 💡 **特别亮点**：支持结合 ChatGPT / Gemini 等 AI 大模型，直接从“培养方案截图”一键生成 JSON 配置，免去手动录入的烦恼！

---

## ✨ 核心特性

- 🔒 **完全本地化与隐私安全**：纯前端单文件应用，无需部署，无后端数据库。所有数据均保存在浏览器的 `localStorage` 中，刷新不丢失。
- 🌗 **日夜双模式 (Dark/Light Mode)**：内置精致的胶囊切换开关，暗黑模式下自带高对比度荧光与描边效果，保护视力。
- 📊 **多彩学分可视化**：
  - **总进度看板**：实时汇总各类学分的完成度。
  - **学期甘特图**：以多彩色块（自带描边隔离）直观展示每个学期的课业压力与学分类型分布。
- 🧮 **智能状态去重与债务高亮**：
  - 完美处理挂科逻辑：标记为“挂科”的课程不会重复计算学分。
  - 必修挂科提醒：在毕业总进度条上，未重修通过的必修课会以**暗红色色块**作为“债务”进行高亮警示。
- ⚙️ **高度可定制化**：无论是留学生的讲座票/活动票要求，还是国内班的人文/创新学分，均可在“设置”面板中手动配置。
- 📦 **数据导入与导出**：支持将当前进度导出为 JSON 备份，或分享给同专业的同学一键恢复。

---

## 🚀 快速开始

本项目为零依赖的单文件应用，无需安装任何 Node.js 环境或构建工具。

1. **下载或克隆本仓库**：
   ```bash
   git clone [https://github.com/你的用户名/你的仓库名.git](https://github.com/你的用户名/你的仓库名.git)

2. **双击打开 credit_tracker.html 文件，即可在任意现代浏览器中使用。**
