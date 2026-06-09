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

---

## 🤖 搭配 AI 一键初始化（推荐）

不想手动一门门添加课程？你可以把培养方案或课表截图发给任意大语言模型（如 ChatGPT, Gemini, Claude），并附上以下标准提示词（Prompt），即可直接生成适配本程序的 JSON 文件：
```
你是一个教务数据提取助手。请阅读我的课表图片，严格按以下 JSON 格式输出，不要输出多余解释文字。

提取规则：
1. student_profile: major 填图片上的专业名称。
2. credit_requirements: 提取培养方案中毕业要求所需的各分类总学分。
3. second_classroom: 提取第二课堂的讲座票和活动票要求数量（如无要求可填 0）。
4. courses: 提取所有课程。字段：course_name(名称), credits(学分，浮点数), category(从 public_mandatory, public_general, major_mandatory, major_elective, practical_teaching 选一), suggested_semester(建议开课学期，数字1-8，不确定填0)。

输出格式模板：
{
  "student_profile": { "major": "软件工程" },
  "credit_requirements": { "public_mandatory": 36.0, "public_general": 39.0, "major_mandatory": 44.0, "major_elective": 15.0, "practical_teaching": 36.0 },
  "second_classroom": { "lecture_tickets_required": 8, "activity_tickets_required": 6 },
  "courses": [ { "course_name": "高等数学", "credits": 4.0, "category": "public_mandatory", "suggested_semester": 1 } ]
}
```

操作步骤：
1. 将 AI 生成的代码保存为 data.json。

2. 在页面中点击 “导入 JSON” 按钮，选中该文件。

3. 一秒完成四年学分框架的搭建！

---

## 🛠️ 数据结构说明 (JSON Schema)

对于想要手动修改或扩展数据的开发者，本程序使用的数据结构如下：
```
{
  "student_profile": {
    "major": "你的专业名称"
  },
  "credit_requirements": {
    "public_mandatory": 36.0,       // 公共基础课（必修）
    "public_general": 39.0,         // 公共基础课（通识）
    "major_mandatory": 44.0,        // 专业基础课（必修）
    "major_elective": 15.0,         // 专业基础课（选修）
    "practical_teaching": 36.0      // 集中实践教学
  },
  "second_classroom": {
    "lecture_tickets_required": 8,  // 讲座票要求
    "activity_tickets_required": 6  // 活动票要求
  },
  "courses": [
    {
      "course_name": "课程名称",
      "credits": 3.0,
      "category": "major_mandatory",
      "suggested_semester": 1,
      "status": "planned"           // 可选状态: planned(未修), progress(修读中), passed(已通过), failed(挂科), retaken(重修通过)
    }
  ]
}
```

---

## 🤝 参与贡献

如果你有更好的 UI 设计想法，或是想为学分计算逻辑添加新的功能（比如：自动计算 GPA 绩点模块），欢迎提交 Pull Request 或发布 Issue！

1. Fork 本仓库

2. 创建你的特性分支 (git checkout -b feature/AmazingFeature)

3. 提交你的更改 (git commit -m 'Add some AmazingFeature')

4. 推送到分支 (git push origin feature/AmazingFeature)

5. 开启一个 Pull Request

📄 开源协议
本项目基于 MIT License 开源，你可以自由地修改、分发及用于个人学习。
