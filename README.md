# CPT304 软件工程 — Wiki 知识库

> 一个面向 CPT304 软件工程课程、持续演进的网状知识库，基于 [Karpathy Wiki 方法论](https://github.com/karpathy) 构建——LLM 负责编写和维护 Wiki，你负责阅读、探索和提出正确的问题。

---

## 目录

- [架构总览](#架构总览)
- [如何使用本 Wiki](#如何使用本-wiki)
- [Wiki 结构](#wiki-结构)
- [工作流程](#工作流程)
- [技巧与提示](#技巧与提示)
- [常见问题](#常见问题)

---

## 架构总览

知识库采用**三层架构**：

```
原始资料                          Wiki 层                           你
(Clippings/)                       (wiki/)                          (Obsidian)
┌─────────────────┐         ┌────────────────────────┐         ┌────────────────┐
│ lecture 1.md     │  整合   │  index.md              │  阅读   │                │
│ lecture 2.md     │ ──────► │  software-crisis.md    │ ──────► │  浏览页面       │
│ lecture 3.md     │         │  solid-principles.md   │         │  跟踪链接       │
│ ...              │         │  design-patterns.md    │         │  图谱视图       │
│ lecture 9.md     │         │  ... (22 个文件)       │         │  提问           │
└─────────────────┘         └────────────────────────┘         └────────────────┘
      ▲                               ▲                                ▲
      │                               │                                │
  不可变（永不修改）             LLM 生成（Agent 维护）          你策展与探索
```

| 层级 | 描述 | 维护者 |
|------|------|--------|
| **原始资料** (`Clippings/`) | Gemini 处理后的课件笔记 | 你（添加新材料） |
| **Wiki 层** (`wiki/`) | 结构化、相互链接的 Markdown 页面 | LLM Agent（我） |
| **Schema** (`wiki/_schema.md`) | 维护规范和工作流程 | 我们共同演化 |

核心思路：**知识一次性编译并持续更新**，而非每次提问重新推导。交叉引用已就位，矛盾已标注，综合观点已反映你的全部阅读内容。

---

## 如何使用本 Wiki

### 🧭 导航

**从索引开始**：打开 [[wiki/index]] —— 它按主题模块列出每个页面并附有一句话摘要。

**跟踪 Wiki 链接**：多数页面使用 `[[wiki/page-name]]` 语法链接到相关概念。点击任意链接直接跳转。

**使用 Obsidian 图谱视图**：打开图谱视图（macOS 下 Cmd+Shift+G）查看所有主题的连接关系。这是发现概念间联系的最佳方式。

### 📖 推荐阅读路径

如果你是课程新手，按此顺序浏览 Wiki：

```
 1. [[wiki/software-crisis]]          → 软件工程为何重要
 2. [[wiki/oop-concepts]]             → 面向对象基础
 3. [[wiki/solid-principles]]         → 设计原则
 4. [[wiki/design-patterns]]          → 基于模式的设计方法
 5. [[wiki/creational-patterns]]      → 创建型设计模式
 6. [[wiki/structural-patterns]]      → 结构型设计模式
 7. [[wiki/behavioral-patterns]]      → 行为型设计模式
 8. [[wiki/software-reuse]]           → 复用策略
 9. [[wiki/component-based-engineering]] → CBSE 与 Spring Boot
10. [[wiki/critical-analysis]]        → 质量分析
11. [[wiki/fmea]]                     → FMEA 深入
12. [[wiki/rca-and-fta]]              → RCA 与故障树分析
13. [[wiki/open-source-software]]     → 开源软件概念
14. [[wiki/software-testing]]         → 测试基础
15. [[wiki/boundary-value-testing]]   → 边界值测试
16. [[wiki/equivalence-class-testing]] → 等价类测试
17. [[wiki/decision-table-testing]]   → 决策表测试
```

### 🔍 搜索

**在 Obsidian 中**：使用内置搜索（Cmd+Shift+F）搜索所有 Wiki 页面。

**使用 Dataview**：若安装了 Obsidian Dataview 插件，可以运行如下查询：

```dataview
TABLE tags, source
FROM "wiki"
SORT file.name ASC
```

### 📚 跨章节概念

部分概念跨越多个课程模块，有独立的专题页面：

- [[wiki/concepts/cohesion-and-coupling]] — 出现在 OOP、SOLID、设计模式和 CBSE 中
- [[wiki/concepts/dependency-injection]] — Spring Boot、SOLID（DIP）和框架概念的核心

---

## Wiki 结构

```
wiki/
├── _schema.md                         ← LLM Agent 维护指南
├── index.md                           ← 主目录索引
├── log.md                             ← 仅追加的活动日志
│
├── software-crisis.md                 # 第 1 讲
├── oop-concepts.md                    # 第 2 讲
├── solid-principles.md                # 第 2 讲
├── design-patterns.md                 # 第 3、4 讲
├── creational-patterns.md             # 第 3 讲
├── structural-patterns.md             # 第 3 讲
├── behavioral-patterns.md             # 第 4 讲
├── software-reuse.md                  # 第 5 讲
├── critical-analysis.md               # 第 6 讲
├── fmea.md                            # 第 6 讲
├── rca-and-fta.md                     # 第 6 讲
├── component-based-engineering.md     # 第 7 讲
├── open-source-software.md            # 第 8 讲
├── software-testing.md                # 第 9 讲
├── boundary-value-testing.md          # 第 9 讲
├── equivalence-class-testing.md       # 第 9 讲
├── decision-table-testing.md          # 第 9 讲
│
└── concepts/
    ├── cohesion-and-coupling.md       # 跨章节概念
    └── dependency-injection.md        # 跨章节概念
```

每个页面包含：
- **YAML frontmatter** — 标签和来源讲次引用
- **概述** — 一段话摘要
- **结构化内容** — 表格、列表、代码块等
- **习题示例** — 真实的考试风格题目与解答
- **相关页面** — 指向关联概念的 Wiki 链接
- **来源** — 指向原始课件文件的链接

### 页面命名约定

- 使用 `kebab-case` 命名以保持一致性
- 按主题命名而非按讲次数命名——概念页面独立于其来源讲次
- 跨章节概念放在 `concepts/` 子目录中

---

## 工作流程

### 📥 整合新资料

当你有**新的课程内容**（新课件、补充笔记、外部文章）时：

1. 将原始 Markdown 文件放入 `Clippings/`
2. 告诉我：*"请将新课件 Clippings/lecture-10.md 整合进 Wiki"*
3. 我会：
   - 读取新资料
   - 按需更新现有 Wiki 页面
   - 为新概念创建新页面
   - 在 `index.md` 中添加新页面条目
   - 在 `log.md` 中追加记录

### ❓ 提问

你可以随时基于 Wiki 向我提问：

- *"解释 SOLID 原则中的 LSP，给出例子"*
- *"FMEA 和 FTA 有什么区别？什么场景用哪个？"*
- *"帮我总结设计模式中创建型、结构型、行为型的区别"*
- *"比较 Spring Boot 依赖注入的三种方式"*

我会搜索 Wiki 页面，综合相关信息，并附上来源页面引用给出答案。

### 🧹 健康检查（Lint）

定期让我检查 Wiki 的健康状况：

- *"检测 wiki 中有无矛盾的表述"*
- *"检查有哪些孤儿页面（没有被其他页面引用）"*
- *"看看有哪些重要概念提到过但没有独立页面"*

这能确保 Wiki 在增长过程中保持健康。

### 📝 将答案归档

当我给出包含深入分析的答案时，你可以要求：

- *"把这个对比结果存成新的 wiki 页面"*

这样，有价值的探索就会积累到知识库中，而非消失在聊天历史里。

---

## 技巧与提示

### 给 Obsidian 用户

| 功能 | 操作方法 |
|------|----------|
| **快速导航** | Cmd+O（macOS）/ Ctrl+O（Windows），输入页面名称 |
| **图谱视图** | Cmd+Shift+G → 查看所有主题的连接关系 |
| **反向链接** | 打开反向链接面板，查看哪些页面链接到当前页面 |
| **搜索** | Cmd+Shift+F — 搜索所有 Wiki 内容 |
| **Dataview 查询** | 使用 `dataview` 代码块从 frontmatter 创建动态表格 |

### 给 Claude Code

当你与我一起维护这个 Wiki 时：

- **Schema 文件** (`wiki/_schema.md`) 告诉我约定规范——帮助我保持一致性
- **索引文件**帮助我快速定位相关页面
- **日志文件**帮助我了解最近的变更

如果希望我在未来的会话中继续维护此 Wiki，以这句话开始：

> *"请读取 wiki/_schema.md 然后继续维护 CPT304 知识库"*

---

## 常见问题

### 我可以手动编辑 Wiki 页面吗？

**可以。** 这是你的知识库——你可以编辑任何内容。Wiki 专为 LLM 维护而设计，但手动编辑不会破坏任何东西。只需注意，未来的 LLM 维护可能会覆盖结构化更新所涉及的部分内容。

### 如果在 Wiki 页面中发现错误怎么办？

向我指出：*"wiki/xxx.md 中有一个错误..."*  我会修复并更新 `log.md`。

### 这和直接保留课件笔记有什么区别？

Wiki **跨讲次整合知识**——第 2 讲的概念（如耦合性）在第 7 讲（CBSE）中被引用。Wiki 通过交叉链接和专题概念页面将知识点编织在一起，而无需在多个文件之间来回切换。

### 我可以添加外部资源吗？

当然。将文章、YouTube 转录稿或补充材料放入 `Clippings/`，然后让我整合到相关的 Wiki 页面中。

### 没有 Claude Code 时 Wiki 还能用吗？

能。Wiki 是纯 Markdown 文件集合，使用 Obsidian Wiki 链接。它可以在任何 Markdown 编辑器中打开，在 Obsidian 中功能完整。LLM Agent（我）是可选的——用于维护，而非基础阅读。

---

<div align="center">

**祝你学习愉快！🎓**

*本 Wiki 包含 22 个页面，覆盖 9 次课程内容，基于约 3,680 行结构化知识构建。*

</div>
