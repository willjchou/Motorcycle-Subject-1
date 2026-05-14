# 摩托车D照考试指南网站 — 产品规格文档 (Spec)

> 版本: v1.0 | 日期: 2026-05-14 | 适用: 2026年5月新规

---

## 1. 项目概述

### 1.1 目标
构建一个**完整的摩托车D照考试指南网站**，覆盖科目一到科目四全部内容，帮助考生系统复习、顺利通过考试。

### 1.2 目标用户
- 苏州地区增驾D照的摩托车学员
- 已有C照、需要增驾摩托车的人群
- 移动端为主要访问场景（微信分享、手机浏览器）

### 1.3 核心原则
- **便携性**: 每个页面可独立打开、离线可用、方便微信分享
- **一致性**: 四个科目统一设计语言和组件体系
- **实用性**: 速记口诀、技巧总结、备考计划为核心价值
- **打印友好**: 支持打印输出，方便纸质复习

### 1.4 技术约束
- 纯静态 HTML + CSS + 极简 JS，无框架依赖
- 引用 Google Fonts（Noto Serif SC / Noto Sans SC）
- 公共样式提取到 `common.css`，各页面引用
- 页面最大宽度 820px，适配移动端
- 需打印时使用 `@media print` 优化

---

## 2. 信息架构

### 2.1 站点结构

```
index.html      → 首页导航（四科目入口 + 考试概览）
k1.html         → 科目一：道路交通安全法律、法规和相关知识
k2.html         → 科目二：场地驾驶技能考试
k3.html         → 科目三：道路驾驶技能考试
k4.html         → 科目四：安全文明驾驶常识
```

### 2.2 首页导航结构

```
┌─────────────────────────────────────┐
│           封面区域                    │
│   2026年 摩托车D照 全科考试指南      │
│   苏州增驾适用 · 基于最新题库         │
├─────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐         │
│  │  科目一   │  │  科目二   │         │
│  │  理论考试 │  │  场地技能 │         │
│  │  50题/90分│  │  80分及格 │         │
│  └──────────┘  └──────────┘         │
│  ┌──────────┐  ┌──────────┐         │
│  │  科目三   │  │  科目四   │         │
│  │  道路技能 │  │  文明常识 │         │
│  │  90分及格 │  │  50题/90分│         │
│  └──────────┘  └──────────┘         │
├─────────────────────────────────────┤
│         考试流程总览图                │
│  科目一 → 科目二 → 科目三 → 科目四   │
│  合格    合格     合格     合格       │
├─────────────────────────────────────┤
│         考试基本信息速查              │
│  年龄要求 / 增驾条件 / 报名材料      │
└─────────────────────────────────────┘
```

---

## 3. 各科目内容大纲

### 3.1 科目一 — k1.html（已有，需重构）

**考试信息**: 50题 | 100分 | 90分及格 | 45分钟 | 判断题+单选题

**内容大纲** (10个section，已确定):

| # | Section | 内容 | 占比 |
|---|---------|------|------|
| 01 | 考试基本信息 | 考试形式、题目、及格、补考规则 | — |
| 02 | 道路交通安全法律法规 | 驾证管理、法规数字、处罚规定 | 30% |
| 03 | 交通信号 | 信号灯、标志识别、标线 | 25% |
| 04 | 安全行车常识 | 摩托车安全要点、让行规则 | 20% |
| 05 | 文明驾驶与应急处置 | 文明原则、事故处理、急救 | 15% |
| 06 | 车辆结构与维护 | 基本结构、日常维护 | 10% |
| 07 | 答题技巧总结 | 判断题技巧、选择题技巧 | — |
| 08 | 速记口诀集 | 能见度口诀、停车距离、速度口诀 | — |
| 09 | 2026年新增重点 | 新规考点、零容错政策 | — |
| 10 | 备考计划与考前提醒 | 三周计划、考前清单 | — |

### 3.2 科目二 — k2.html（新建）

**考试信息**: 满分100分 | 80分及格 | 计算机自动评判

**内容大纲** (8个section):

| # | Section | 内容要点 |
|---|---------|----------|
| 01 | 考试基本信息 | 考试形式、及格线、评判标准、补考规则 |
| 02 | 摩托车场地布局总览 | SVG 示意图：科目二考场全景，标注各项目位置 |
| 03 | 绕桩（桩考） | **SVG 绕桩路线图**、操作要领（车速、转向、离合）、常见扣分点、口诀 |
| 04 | 坡道定点停车和起步 | **SVG 坡道示意图**、定点标准、起步步骤（手刹/油离配合）、扣分项 |
| 05 | 单边桥 | 操作要领、平衡控制、通过技巧 |
| 06 | 直角转弯 | 转弯时机、打方向要点、车身出线判定 |
| 07 | 档位操作与加减档 | 档位示意图（SVG）、换档时机、拖档/跳档扣分 |
| 08 | 通用技巧与备考 | 离合控制练习、考前熟悉场地、心态调整 |

### 3.3 科目三 — k3.html（新建）

**考试信息**: 满分100分 | 90分及格 | 随车评判仪实时打分

**内容大纲** (9个section):

| # | Section | 内容要点 |
|---|---------|----------|
| 01 | 考试基本信息 | 考试形式、评判方式、及格线、路线概述 |
| 02 | 考试路线总览 | **SVG 路线示意图**：标注各考核路段（起步、变道、超车、路口等） |
| 03 | 起步与靠边停车 | 起步步骤（打灯→观察→鸣号→挂挡→松手刹）、靠边停车规范（30cm） |
| 04 | 变更车道与超车 | 变道步骤（灯→镜→转→灯）、超车步骤、禁止超车情形 |
| 05 | 通过路口与特殊路段 | 信号灯路口、人行横道、学校区域、公交站 |
| 06 | 直线行驶与加减档 | 保持直线、档位与速度匹配、不拖档 |
| 07 | 掉头与夜间行驶 | 掉头规定、灯光使用（近远光切换） |
| 08 | **扣分速查表** | 所有扣分项一览（扣5分/10分/100分项），用表格+颜色标注严重程度 |
| 09 | 通用技巧与备考 | 考前熟悉路线、灯光模拟考试技巧、心态管理 |

### 3.4 科目四 — k4.html（新建）

**考试信息**: 50题 | 100分 | 90分及格 | 判断题+单选题+**多选题** | 45分钟

**内容大纲** (9个section):

| # | Section | 内容要点 |
|---|---------|----------|
| 01 | 考试基本信息 | 考试形式、题目类型（含多选题）、及格线、与科目一的区别 |
| 02 | 恶劣天气驾驶 | 雨天/雾天/冰雪/大风 — 安全驾驶要点 |
| 03 | 高速公路驾驶 | 高速公路特有规则、安全车距、速度管理 |
| 04 | 紧急情况处置 | 爆胎/制动失灵/火灾/碰撞 — 应急步骤 |
| 05 | 伤员急救 | 心肺复苏/止血/骨折/烧伤 — 急救流程 |
| 06 | 文明驾驶行为 | 礼让行人/夜间灯光/安全驾驶道德 |
| 07 | **多选题专项技巧** | 多选题答题策略、常见组合选项规律、排除法 |
| 08 | 速记口诀集 | 恶劣天气口诀、急救口诀、灯光使用口诀 |
| 09 | 备考计划与考前提醒 | 复习建议、错题策略、考试心态 |

---

## 4. 技术规范

### 4.1 CSS 变量体系（复用科目一）

```css
:root {
  --bg: #faf8f4;          /* 页面背景 */
  --surface: #ffffff;     /* 卡片/区块背景 */
  --accent: #c0392b;      /* 主强调色（深红） */
  --accent-light: #fdecea;/* 浅强调背景 */
  --accent-secondary: #2c3e50; /* 副强调色（深蓝灰） */
  --text-primary: #1a1a1a;
  --text-body: #333333;
  --text-muted: #6b6b6b;
  --border: #e0dbd3;
  --border-light: #f0ece6;
  /* 标签色彩系统 */
  --tag-blue: #1a5276; --tag-blue-bg: #eaf2f8;
  --tag-green: #1e6e3e; --tag-green-bg: #e8f6ef;
  --tag-orange: #7d5a00; --tag-orange-bg: #fef9e7;
  --tag-purple: #5b2c6f; --tag-purple-bg: #f4ecf7;
  --tag-red: #922b21; --tag-red-bg: #fdedec;
}
```

### 4.2 新增科目色彩编码（用于科目区分）

| 科目 | 色彩 | 用途 |
|------|------|------|
| 科目一 | `--accent` (红) | 已有 |
| 科目二 | `--tag-blue` | 封面强调、section 编号 |
| 科目三 | `--tag-green` | 封面强调、section 编号 |
| 科目四 | `--tag-orange` | 封面强调、section 编号 |

### 4.3 字体

```
标题: 'Noto Serif SC', serif    (400, 700, 900)
正文: 'Noto Sans SC', sans-serif (300, 400, 500, 700)
CDN: fonts.googleapis.com
```

### 4.4 响应式

- 最大宽度 820px，水平居中
- 移动端自动适配（padding 缩减，tip-grid 改为单列）
- `viewport` meta 必须设置

### 4.5 打印优化

- 隐藏 back-to-top 按钮
- 封面和 section 避免分页断裂
- 颜色保持（`print-color-adjust: exact`）

---

## 5. 组件清单

### 5.1 已有组件（提取到 common.css）

| 组件 | CSS Class | 用途 |
|------|-----------|------|
| 封面 | `.cover` | 每科封面页 |
| 目录 | `.toc` | 章节导航 |
| 章节标题 | `.section`, `.section-header`, `.section-num` | 内容分区 |
| 数据表格 | `.data-table` | 知识对照表 |
| 提示块 | `.callout`, `.callout-{color}` | 速记要点 |
| 口诀框 | `.mnemonic-box` | 口诀记忆 |
| 双栏卡片 | `.tip-grid`, `.tip-card` | 要点对比 |
| 计划表 | `.plan-table` | 训练计划 |
| 颜色图例 | `.color-chart` | 标志颜色说明 |
| 清单 | `.checklist` | 考前检查项 |
| 页脚 | `.footer-note` | 页脚声明 |
| 分隔线 | `.divider` | 区块分隔 |
| 回顶部 | `.back-to-top` | 固定按钮 |

### 5.2 新增组件（写入 common.css）

| 组件 | CSS Class | 用途 | 使用场景 |
|------|-----------|------|----------|
| 导航栏 | `.site-nav` | 首页+各科间的顶部导航 | 所有页面 |
| 科目卡片 | `.subject-card` | 首页四科目入口卡片 | 首页 |
| SVG 图示容器 | `.diagram-box` | 包裹 SVG 场地/路线图 | 科目二、科目三 |
| 扣分表格 | `.deduct-table` | 扣分项速查（红/橙/灰三级） | 科目三 |
| 步骤条 | `.step-flow` | 操作步骤可视化 | 科目二、科目三 |

### 5.3 新增组件设计规范

#### 导航栏 `.site-nav`
```css
.site-nav {
  position: sticky; top: 0; z-index: 100;
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  padding: 12px 0;
}
.site-nav-inner {
  max-width: 820px; margin: 0 auto; padding: 0 50px;
  display: flex; align-items: center; justify-content: space-between;
}
.site-nav .logo {
  font-family: 'Noto Serif SC', serif; font-weight: 700;
  font-size: 16px; color: var(--accent);
  text-decoration: none;
}
.site-nav .nav-links {
  display: flex; gap: 20px; font-size: 13px;
}
.site-nav .nav-links a {
  color: var(--text-muted); text-decoration: none;
  padding: 4px 8px; border-radius: 4px;
  transition: all 0.2s;
}
.site-nav .nav-links a:hover,
.site-nav .nav-links a.active {
  color: var(--accent); background: var(--accent-light);
}
```

#### SVG 图示容器 `.diagram-box`
```css
.diagram-box {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 24px;
  margin-bottom: 20px;
  text-align: center;
  overflow-x: auto;
}
.diagram-box svg {
  max-width: 100%; height: auto;
}
.diagram-box .diagram-title {
  font-weight: 700; color: var(--accent-secondary);
  margin-bottom: 16px; font-size: 14px;
}
```

#### 扣分表格 `.deduct-table`
```css
.deduct-table {
  /* 继承 .data-table 基础样式 */
  /* 特殊：扣分值用颜色区分严重程度 */
  /* -100分（直接不合格）: 红色背景 */
  /* -10分（一般扣分）: 橙色背景 */
  /* -5分（轻微扣分）: 灰色背景 */
}
.deduct-100 { background: var(--tag-red-bg) !important; }
.deduct-10 { background: var(--tag-orange-bg) !important; }
.deduct-5 { background: #f5f5f5 !important; }
```

#### 步骤条 `.step-flow`
```css
.step-flow {
  display: flex; align-items: center; gap: 0;
  margin-bottom: 20px; flex-wrap: wrap;
}
.step-item {
  display: flex; align-items: center; gap: 8px;
  padding: 10px 16px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 6px;
  font-size: 13px;
}
.step-num {
  width: 24px; height: 24px;
  background: var(--accent); color: #fff;
  border-radius: 50%; display: flex;
  align-items: center; justify-content: center;
  font-size: 12px; font-weight: 700;
  flex-shrink: 0;
}
.step-arrow {
  color: var(--border); font-size: 16px;
  margin: 0 4px; flex-shrink: 0;
}
```

---

## 6. 文件结构

```
C:\Users\zhouwenji\Desktop\openclaw\科目一\
├── index.html      ← 首页导航（新）
├── common.css      ← 公共样式（新）
├── spec.md         ← 本规格文档
├── k1.html         ← 科目一（从现有 index.html 迁移）
├── k2.html         ← 科目二（新）
├── k3.html         ← 科目三（新）
└── k4.html         ← 科目四（新）
```

### 文件命名规范
- HTML: `k{科目编号}.html`（k1, k2, k3, k4）
- CSS: `common.css`（公共样式）
- 页面标题格式: `2026年摩托车D照科目X — {副标题}`
- 页面内部 ID: `sec-{两位编号}`（sec-01, sec-02...）

---

## 7. 实施路线图

| 阶段 | 内容 | 产出 |
|------|------|------|
| **Step 1** | 编写 Spec 文档 | `spec.md` ← 当前 |
| **Step 2** | 提取公共 CSS | `common.css` |
| **Step 3** | 重构科目一 + 创建首页 | `k1.html` + `index.html` |
| **Step 4** | 创建科目二 | `k2.html`（含 SVG 场地图） |
| **Step 5** | 创建科目三 | `k3.html`（含 SVG 路线图 + 扣分表） |
| **Step 6** | 创建科目四 | `k4.html`（含多选题技巧） |
