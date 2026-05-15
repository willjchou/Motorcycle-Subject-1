# 摩托车D照考试指南网站 — 产品规格文档

> 版本: v1.1 | 更新: 2026-05-15 | 适用: 2026年5月新规 | 状态: **已完成实现**

---

## 1. 项目概述

### 1.1 定位

面向**苏州地区增驾D照摩托车学员**的全科考试复习指南，覆盖科目一到科目四，以移动端浏览为主要场景。

### 1.2 核心价值

- **速记口诀**：各科目均提供归纳式记忆口诀
- **图解说明**：科目二、三含 SVG 手绘场地/路线示意图
- **扣分速查**：科目二、三含扣分项颜色分级表
- **多选技巧**：科目四专项多选题答题策略
- **打印友好**：每个页面可直接打印作为纸质复习材料

### 1.3 技术约束

| 项目 | 约束 |
|------|------|
| 技术栈 | 纯静态 HTML + CSS，无 JS 框架 |
| 字体 | Google Fonts（Noto Serif SC / Noto Sans SC） |
| 样式管理 | 公共样式 `common.css`；各页面通过内联 `<style>` 覆盖主题色 |
| 页面宽度 | 最大 820px，水平居中 |
| 响应式 | `@media (max-width: 600px)` 单列布局 |
| 打印 | `@media print` + `print-color-adjust: exact` |
| 滚动定位 | `scroll-margin-top: 60px`（规避粘性导航遮挡） |

---

## 2. 文件结构

```
C:\Users\zhouwenji\Desktop\openclaw\科目一\
├── index.html      首页导航（四科目入口 + 考试概览）
├── common.css      公共样式表（组件库 + 响应式 + 打印）
├── k1.html         科目一：道路交通安全法律、法规和相关知识
├── k2.html         科目二：场地驾驶技能考试
├── k3.html         科目三：道路驾驶技能考试
├── k4.html         科目四：安全文明驾驶常识
├── README.md       GitHub 项目说明
└── spec.md         本规格文档
```

### 文件命名规范

- HTML 页面：`k{n}.html`（n = 1-4）
- 页面 `<title>` 格式：`2026年摩托车D照科目X — {副标题}`
- 章节锚点 ID：`sec-{两位编号}`（`sec-01`, `sec-02` ...）

---

## 3. 信息架构

### 3.1 站点导航

所有页面顶部均有粘性导航栏（`position: sticky; top: 0`），包含：
- Logo "D照指南"（链接至 `index.html`）
- 四个科目链接，当前页添加 `.active` 类

### 3.2 首页 `index.html`

```
封面区域（.home-cover）
  ↳ 标题：摩托车D照 全科考试指南
  ↳ 副标题：2026年5月新规适用 · 苏州增驾参考

快速信息（.home-quick-info，3格）
  ↳ 4个考试科目 / 18+ 年龄要求 / D 准驾车型

四科目卡片（.subject-grid，2×2）
  ↳ 科目一（红色）→ k1.html
  ↳ 科目二（蓝色）→ k2.html
  ↳ 科目三（绿色）→ k3.html
  ↳ 科目四（橙色）→ k4.html

考试流程总览（.process-flow）
  ↳ 科目一 →（100分）→ 科目二 →（100分）→ 科目三 →（100分）→ 科目四（100分）

考试基本信息（.data-table，7行）
  ↳ 准驾车型、年龄要求、身体条件、增驾条件、报名材料、考试预约、补考规则

D照须知（.tip-grid，4卡）
  ↳ 骑行装备 / 禁止事项 / 路权规则 / 苏州当地提示
```

---

## 4. 各科目规格

### 4.1 科目一 `k1.html`

| 项目 | 值 |
|------|----|
| 主题色 | `--accent` #c0392b（红色） |
| 封面渐变 | 默认深色（common.css `.cover`） |
| 考试形式 | 笔试，50题，100分制，90分及格，45分钟 |
| 题型 | 判断题 + 单选题，图标题零容错 |

**章节列表（10节）：**

| ID | 章节名 |
|----|--------|
| sec-01 | 考试基本信息 |
| sec-02 | 道路交通安全法律法规 |
| sec-03 | 交通信号（标志·标线·信号灯） |
| sec-04 | 安全行车常识 |
| sec-05 | 文明驾驶与应急处置 |
| sec-06 | 车辆结构与维护常识 |
| sec-07 | 答题技巧总结 |
| sec-08 | 速记口诀集 |
| sec-09 | 2026年新增重点考点 |
| sec-10 | 备考计划与考前提醒 |

---

### 4.2 科目二 `k2.html`

| 项目 | 值 |
|------|----|
| 主题色 | `--tag-blue` #1a5276（蓝色） |
| 封面渐变 | `linear-gradient(135deg, #0a1628, #1a3a5c, #0d4f8b)` |
| 考试形式 | 场地实操，满分100分，80分及格，计算机自动评判 |

**章节列表（8节）：**

| ID | 章节名 | 特殊组件 |
|----|--------|----------|
| sec-01 | 考试基本信息 | — |
| sec-02 | 场地布局总览 | SVG 考场全景图（680×260） |
| sec-03 | 绕桩（桩考） | SVG 绕桩路线图（680×200）+ 步骤条 |
| sec-04 | 坡道定点停车和起步 | SVG 坡道示意图（680×200）+ 步骤条 |
| sec-05 | 单边桥 | 步骤条 |
| sec-06 | 直角转弯 | 步骤条 |
| sec-07 | 档位操作与加减档 | SVG 档位图（680×160） |
| sec-08 | 通用技巧与备考 | 备考计划表 |

**主题色覆盖（页内 `<style>`）：**
```css
.section-header { border-bottom-color: var(--tag-blue); }
.section-num { color: var(--tag-blue); }
.sub-section h3 { border-left-color: var(--tag-blue); }
.plan-table thead th { background: var(--tag-blue); }
.plan-table .day-cell { color: var(--tag-blue); }
.diagram-box .diagram-title { color: var(--tag-blue); }
.step-num { background: var(--tag-blue); }
.deduct-table thead th { background: var(--tag-blue); }
```

---

### 4.3 科目三 `k3.html`

| 项目 | 值 |
|------|----|
| 主题色 | `--tag-green` #1e6e3e（绿色） |
| 封面渐变 | `linear-gradient(135deg, #0a1a0f, #163020, #0d5a25)` |
| 考试形式 | 道路实操，满分100分，90分及格，随车评判仪实时打分 |

**章节列表（9节）：**

| ID | 章节名 | 特殊组件 |
|----|--------|----------|
| sec-01 | 考试基本信息 | — |
| sec-02 | 考试路线总览 | SVG 路线示意图（680×300） |
| sec-03 | 起步与靠边停车 | 步骤条 |
| sec-04 | 变更车道与超车 | 步骤条 |
| sec-05 | 通过路口与特殊路段 | 提示块 |
| sec-06 | 直线行驶与加减档 | — |
| sec-07 | 掉头与夜间行驶 | 提示块 |
| sec-08 | 扣分速查表 | `.deduct-table`（红/橙/灰三级） |
| sec-09 | 通用技巧与备考 | 备考计划表 |

**扣分等级说明：**

| 等级 | 行背景类 | 分值标签类 | 含义 |
|------|---------|-----------|------|
| 严重 | `.deduct-100` | `.dv-100`（红底白字） | 直接不合格 |
| 一般 | `.deduct-10` | `.dv-10`（橙底白字） | 扣10分 |
| 轻微 | `.deduct-5` | `.dv-5`（灰底） | 扣5分 |

---

### 4.4 科目四 `k4.html`

| 项目 | 值 |
|------|----|
| 主题色 | `--tag-orange` #7d5a00（橙色） |
| 封面渐变 | `linear-gradient(135deg, #1a1a0a, #3d3020, #5a4d0d)` |
| 考试形式 | 笔试，50题，100分制，90分及格，45分钟，含多选题 |

**章节列表（9节）：**

| ID | 章节名 | 特殊内容 |
|----|--------|----------|
| sec-01 | 考试基本信息 | 多选题计分规则说明 |
| sec-02 | 恶劣天气驾驶 | 雨天/雾天/冰雪/大风四分类 |
| sec-03 | 高速公路驾驶 | 速度规定、安全距离 |
| sec-04 | 紧急情况处置 | 爆胎/制动失灵/火灾/碰撞 |
| sec-05 | 伤员急救 | 心肺复苏/止血/骨折/烧伤流程 |
| sec-06 | 文明驾驶行为 | 礼让行人、灯光使用 |
| sec-07 | 多选题专项技巧 | 常见组合规律、排除法、陷阱选项 |
| sec-08 | 速记口诀集 | 恶劣天气/急救/灯光口诀 |
| sec-09 | 备考计划与考前提醒 | 错题策略、考试心态 |

---

## 5. CSS 架构

### 5.1 CSS 变量（`common.css :root`）

```css
/* 背景与表面 */
--bg: #faf8f4;
--surface: #ffffff;

/* 主强调色（科目一/全站） */
--accent: #c0392b;
--accent-light: #fdecea;
--accent-secondary: #2c3e50;

/* 文字 */
--text-primary: #1a1a1a;
--text-body: #333333;
--text-muted: #6b6b6b;

/* 边框 */
--border: #e0dbd3;
--border-light: #f0ece6;

/* 标签色系 */
--tag-blue: #1a5276;   --tag-blue-bg: #eaf2f8;    /* 科目二 */
--tag-green: #1e6e3e;  --tag-green-bg: #e8f6ef;   /* 科目三 */
--tag-orange: #7d5a00; --tag-orange-bg: #fef9e7;  /* 科目四 */
--tag-purple: #5b2c6f; --tag-purple-bg: #f4ecf7;  /* 备用 */
--tag-red: #922b21;    --tag-red-bg: #fdedec;     /* 扣分标记 */

/* 阴影 */
--shadow-sm: 0 1px 3px rgba(0,0,0,0.06);
--shadow-md: 0 4px 12px rgba(0,0,0,0.08);
```

### 5.2 组件清单

#### 布局与导航

| 组件 | 类名 | 说明 |
|------|------|------|
| 页面容器 | `.page-container` | 最大宽820px，水平居中，padding 40px 50px |
| 粘性导航 | `.site-nav` / `.site-nav-inner` | `position: sticky; top: 0; z-index: 100` |
| 回顶部按钮 | `.back-to-top` / `.visible` | 固定右下角，滚动后出现，打印时隐藏 |

#### 封面

| 组件 | 类名 | 说明 |
|------|------|------|
| 科目页封面 | `.cover` | 深色渐变背景，含 `.badge`、`h1`、`.divider-line`、`.subtitle`、`.meta` |
| 首页封面 | `.home-cover` | 同 `.cover`，无 `.badge` 和 `.meta`，无分页断行 |

#### 首页专用

| 组件 | 类名 | 说明 |
|------|------|------|
| 快速信息格 | `.home-quick-info` / `.quick-info-item` | 3列网格，含 `.qi-value` 和 `.qi-label` |
| 科目卡片 | `.subject-grid` / `.subject-card` | 2×2网格，`.k1`~`.k4` 颜色变体，hover 上浮 |
| 流程节点 | `.process-flow` / `.process-step` | 横向排列，含 `.ps-circle`（彩色圆形）、`.ps-label`、`.ps-check` |
| 流程箭头 | `.process-arrow` | 字符 `→`，padding-bottom 30px 对齐圆形 |

#### 内容结构

| 组件 | 类名 | 说明 |
|------|------|------|
| 目录 | `.toc` / `.toc-list` | CSS 计数器，hover 动画，`.toc-arrow` 右箭头 |
| 章节 | `.section` + `id="sec-XX"` | `scroll-margin-top: 60px` |
| 章节标题 | `.section-header` / `.section-num` / `.section-title` | 底部2px边线，大号序号 |
| 子章节 | `.sub-section` / `h3` / `h4` | `h3` 左3px边线 |

#### 内容块

| 组件 | 类名 | 说明 |
|------|------|------|
| 数据表格 | `.data-table` | 通用知识对照表，表头深色 |
| 提示块 | `.callout` + 变体 | 左4px彩线；`.callout-blue/green/orange/purple/red` |
| 口诀框 | `.mnemonic-box` | 深色渐变背景，金色标题 `#e8c547` |
| 双栏卡片 | `.tip-grid` / `.tip-card` | 2列，`.tip-label` 含4色变体 |
| 颜色图例 | `.color-chart` / `.color-item` / `.color-dot` | 3列网格，彩色圆点 |
| 清单 | `.checklist` | 绿色 ✓ 图标列表 |
| 分隔线 | `.divider` | 1px边框，上下 32px |

#### 科目二/三专用

| 组件 | 类名 | 说明 |
|------|------|------|
| SVG 容器 | `.diagram-box` | 白底，`overflow-x: auto`，`.diagram-title` / `.diagram-note` |
| 扣分表格 | `.deduct-table` | 继承表格样式；`.deduct-100/10/5` 行背景；`.dv-100/10/5` 分值标签 |
| 步骤条 | `.step-flow` / `.step-item` / `.step-num` / `.step-arrow` | 横向，序号圆形，主题色可覆盖 |

#### 备考计划

| 组件 | 类名 | 说明 |
|------|------|------|
| 计划表 | `.plan-table` | 表头用主题色，`.day-cell` 加粗日期列 |

### 5.3 主题色覆盖机制

各科目页通过页内 `<style>` 块覆盖关键组件颜色，无需修改 `common.css`：

```
科目一（k1.html）：不覆盖，使用 common.css 默认的 --accent 红色
科目二（k2.html）：覆盖为 --tag-blue
科目三（k3.html）：覆盖为 --tag-green
科目四（k4.html）：覆盖为 --tag-orange
```

覆盖范围：`.section-header` 底线 / `.section-num` 颜色 / `.sub-section h3` 左线 / `.plan-table` 表头 / `.step-num` 背景 / `.cover` 渐变

---

## 6. SVG 图示规范

所有 SVG 均为内联代码，嵌入 `.diagram-box` 容器内。

| 文件 | SVG | viewBox | 说明 |
|------|-----|---------|------|
| k2.html | 考场全景图 | 0 0 680 260 | 标注绕桩、坡道、单边桥位置 |
| k2.html | 绕桩路线图 | 0 0 680 200 | 蛇形路线箭头 |
| k2.html | 坡道示意图 | 0 0 680 200 | 坡道剖面 + 停车位标注 |
| k2.html | 档位示意图 | 0 0 680 160 | 摩托车换档杆位置图 |
| k3.html | 考试路线图 | 0 0 680 300 | 道路路线 + 各考核点标注 |

SVG 规范：
- `max-width: 100%; height: auto`（响应式）
- 文字使用 `font-family: sans-serif; font-size: 12px`
- 颜色使用 `stroke` / `fill`，不依赖 CSS 变量（SVG 内联安全）

---

## 7. 响应式规范

### 断点：`max-width: 600px`

| 元素 | 桌面 | 移动端 |
|------|------|--------|
| `.home-quick-info` | 3列 | 1列 |
| `.subject-grid` | 2列 | 1列 |
| `.tip-grid` | 2列 | 1列（common.css 全局） |
| `.process-flow` | 横向 | 纵向（`flex-direction: column`） |
| `.process-arrow` | 横向 `→` | 竖向（`rotate(90deg)`） |
| `.page-container` | `padding: 40px 50px` | `padding: 20px 20px` |
| `.color-chart` | 3列 | 2列 |

---

## 8. 打印规范

`@media print` 规则定义在 `common.css` 末尾：

- 隐藏：`.back-to-top`、`.site-nav`
- 禁止分页：`.section`、`.sub-section`、`.callout`、`.mnemonic-box`、`.diagram-box`
- 强制颜色：`-webkit-print-color-adjust: exact; print-color-adjust: exact`（body 级别）
- 封面强制换页：`.cover { page-break-after: always }`、`.toc { page-break-after: always }`

---

## 9. 部署信息

| 项目 | 值 |
|------|----|
| GitHub 仓库 | https://github.com/willjchou/Motorcycle-Subject-1 |
| 主分支 | `main` |
| 部署方式 | GitHub Pages（静态托管） |
| CNAME | 已配置自定义域名 |
| 最近 Commit | 更新 index.html：流程总览分数改为满分（100分）|
