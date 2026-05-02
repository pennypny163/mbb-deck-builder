# MBB Deck Builder

> 从一个商业问题到一份正式PPT研报，全程自动管理。

你给一个问题，它还你一套 15-25 页的 McKinsey 风格 PPT——含 Issue Tree、数据验证、专业配色、逐页自检，中间不用你操心排版。

---

## 它干什么

把咨询项目的全流程压缩成 90 分钟：

```
你的问题 → 问题拆解 → 假设形成 → 页面设计 → 数据收集 → PPT生成 → 迭代打磨
```

传统做法：3-5天 + 一个分析师团队。
用 Deck Builder：2 小时 + 你一个人。

---

## 它不做什么

- ❌ 不做"帮你想方向"的 brainstorm — 那个用 [MBB Spark Partner](https://github.com/pennypny163/mbb-spark-partner)
- ❌ 不做"快速写篇文字报告" — 那个用 [MBB Draft Distiller](https://github.com/pennypny163/mbb-draft-distiller)
- ❌ 不做通用PPT美化 — 它只做**研究型PPT**（有数据、有分析、有结论）

---

## 8步工作流

```
Phase 1: 拆问题（20-30分钟）
  ┌─ STEP 1: 定义问题边界（是什么 / 不是什么）
  ├─ STEP 2: Issue Tree — MECE拆解
  └─ STEP 3: 假设驱动 — 形成 Hypotheses

Phase 2: 设计页面（30-40分钟）
  ┌─ STEP 4: 确定每页的论证方式
  └─ STEP 5: 设计 Dummy Pages（含依赖关系标注）

Phase 3: 逐页生成（40-60分钟）
  ┌─ STEP 6-7: 逐页循环（搜索→Excel→PPT→自检→确认）
  ├─ STEP 8: 可选 Word 报告
  └─ STEP 9: 迭代优化（配色/密度/对齐）
```

---

## 为什么叫 Deck Builder

因为它的核心产出是 **deck**（PPT），而且是按工程化方式 **build** 出来的：

- 每页有设计蓝图（Dummy Pages）
- 每页有数据规范（Excel Sheet）
- 每页有自检清单（6项通过才放行）
- 页面间有依赖管理（哪些先做、哪些后做）
- 支持断点续写（今天做到第8页，明天接着第9页）

---

## 工程亮点

### 渐进式加载

不一次性读完所有文档，按步骤按需加载：

```
STEP 1:      只用 SKILL.md 核心
STEP 2-3:    临时加载 methodology.md → 用完释放
STEP 4-5:    临时加载 layouts.md + design-specs.md → 用完释放
STEP 6-7:    临时加载 excel-data-spec.md → 逐页处理
```

效果：上下文消耗降低 70%+，可稳定生成 20-25 页。

### 逐页循环

```
对于每一页：
1. 依赖检查（能做吗？前置页完成了吗？）
2. 按 Dummy 设计执行 2-5 次搜索
3. 数据存入 Excel（原始数据 + 来源URL）
4. 生成 PPT 页（严格按设计稿）
5. 自检 6 项
6. 告知用户 → 等确认 → 清空上下文 → 下一页
```

### 跨对话断点续写

```
[新对话]
上传 DummyPages.md + 已完成的PPT/Excel
"请从第10页继续"

→ 自动识别进度，继续循环
```

---

## 设计规范

McKinsey 正统配色和排版：

| 元素 | 规范 |
|------|------|
| 主色 | 深蓝 #002960 |
| 辅色 | 中蓝 #0065BD |
| 强调 | 黄色 #FFDB00 |
| 标题 | 18pt，论点式（一句话结论） |
| 正文 | 11pt |
| 布局 | 7种标准模板 |
| 密度 | 50-70字符/平方英寸 |
| 规则 | 深蓝背景→白色文字 / 大框→直角 / 默认无边框 |

---

## 典型使用场景

| 输入 | 输出（示例） |
|------|-------------|
| "分析中国新能源汽车市场" | 18页：市场规模→竞争格局→驱动因素→洞察建议 |
| "为什么短视频电商增长这么快" | 17页：增长体现→需求侧→供给侧→案例→启示 |
| "分析我们进入XX市场的机会" | 20页：市场评估→玩家分析→能力匹配→进入建议 |

---

## 文件结构

```
mbb-deck-builder/
├── SKILL.md                       # 核心指令（736行，8步流程+架构说明）
├── references/
│   ├── methodology.md             # MECE + Issue Tree + Hypotheses 方法论
│   ├── layouts.md                 # 7种McKinsey页面布局
│   ├── design-specs.md            # 配色/字号/密度规范
│   ├── page-dependencies.md       # 页面依赖关系标注规范
│   ├── excel-data-spec.md         # Excel数据文件结构
│   ├── delivery-summary.md        # Word报告格式
│   ├── troubleshooting.md         # 常见问题解决
│   ├── quick-guide.md             # 快速参考
│   ├── workflow.md                # 详细流程图
│   ├── examples.md                # 完整案例
│   └── V2_vs_V3_comparison.md     # 版本对比
├── LICENSE
└── README.md
```

---

## 安装

### 方式一：直接喂给任何 AI

1. 复制 `SKILL.md` 内容作为 system prompt
2. 把 `references/` 文件夹放在 AI 能读取的位置
3. 开始对话

### 方式二：Claude Code / Cline / Cursor 等

```bash
git clone https://github.com/pennypny163/mbb-deck-builder.git ~/.your-tool/skills/mbb-deck-builder
```

### 方式三：WorkBuddy

```bash
cp -r mbb-deck-builder ~/.workbuddy/skills/
```

---

## 和其他 Skill 的配合

```
MBB Spark Partner（想清楚方向）
       ↓
MBB Draft Distiller（快速出文字报告）
       ↓
MBB Deck Builder（升级为正式PPT）← 你在这里
```

| 先 | 后 | 效果 |
|----|-----|------|
| Spark Partner 做完决策 | → Deck Builder 做 PPT | 从"要不要做"到"交付物" |
| Draft Distiller 写完报告 | → Deck Builder 做 PPT | 文字报告升级为正式deck |
| 直接给 Deck Builder | 一步到位 | 问题→PPT，全自动 |

---

## 版本

| 版本 | 变更 |
|------|------|
| V3.1 | 页面依赖关系标注 + 跨对话续写增强 |
| V3.0 | 渐进式加载架构，上下文消耗降低70% |
| V2.0 | 完整8步工作流 |

## License

MIT
