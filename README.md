# Personal Academic Editor

一个面向学术作者的 AI 审稿与论文检查 Skill，支持中英文稿件，具备领域自适应学习能力。

## 功能概述

### 模块一：稿件检查（Paper Checker）

| 检查项 | 说明 |
|--------|------|
| 引用准确性 | 检查正文引用与参考文献列表一致性、引用格式、引用多样性 |
| 数据真实性 | 检查数字内部一致性、图表与正文对应、统计数值合理性 |
| 编造内容检测 | 检查无法验证的声称、模糊表述、逻辑漏洞、写作风格突变 |
| 语言润色 | 英文检查语法/拼写/学术语气；中文检查病句/错别字/"的地得"/中英混排 |

### 模块二：稿件评估（Paper Evaluator）

| 评估维度 | 说明 |
|----------|------|
| 标题与摘要 | 清晰度、完整性、关键词 |
| 引言 | 研究空白、文献综述、研究问题 |
| 方法 | 研究设计、可重复性、统计方法 |
| 结果 | 呈现清晰度、图表质量 |
| 讨论 | 解释准确性、局限性、未来方向 |
| 创新性与贡献 | 新颖性、学术贡献 |
| 期刊匹配 | 推荐适合投稿的期刊 |

### 领域自适应学习（Domain-Adaptive Learning）

核心特性：Skill 会根据提交稿件的领域**自动学习进化**。

1. **领域检测** — 扫描标题/摘要中的关键词，自动识别稿件所属学科
2. **知识加载** — 从 `domain-knowledge/` 加载该领域的审稿标准和专业知识
3. **专业审稿** — 以领域专家的标准进行审稿
4. **知识更新** — 审稿后从论文中提取新术语、新方法、引用模式，更新领域知识库

预置领域知识：
- 公共管理（Public Administration）
- 社会科学通用（Social Science General）

支持自动识别并学习更多领域。

## 文件结构

```
personal-editor/
├── README.md                         # 项目说明（本文件）
├── SKILL.md                          # 主指令文件，AI agent 加载入口
├── manifest.json                     # 跨平台元数据
├── domain-knowledge/                 # 领域知识库（自动迭代更新）
│   ├── public-admin.json             # 公共管理领域知识
│   └── social-science.json           # 社会科学通用知识
├── templates/                        # 报告模板
│   ├── check-report.md               # 检查报告模板
│   └── evaluation-report.md          # 评估报告模板
└── references/                       # 参考资源
    ├── common-errors.md              # 常见错误案例库
    └── journal-standards.md          # 期刊审稿标准参考
```

## 安装与使用

### Trae IDE

将整个 `personal-editor/` 目录复制到项目的 `.trae/skills/` 下：

```bash
cp -r personal-editor /path/to/your-project/.trae/skills/
```

Trae 会自动加载该 Skill，直接向 AI 发送稿件即可触发。

### Codex

将 `SKILL.md` 的内容作为 system prompt 或 context 加载。

### Cursor

将 `SKILL.md` 的内容复制到 `.cursorrules` 文件中，或在 Cursor 设置中添加为自定义指令。

### Windsurf

将 `SKILL.md` 的内容作为 system prompt 加载。

### WorkBuddy

在 WorkBuddy 中导入 `SKILL.md` 作为自定义 Skill。

## 使用方式

直接将论文内容（中文或英文）发送给 AI agent，Skill 会自动：

1. 检测稿件语言（中/英文），用相同语言回复
2. 检测稿件所属领域，加载对应知识库
3. 默认执行**全面审查**（检查 + 评估）
4. 输出结构化报告，包含严重问题、修改建议和评分
5. 更新领域知识库，下次审阅同领域稿件时更专业

也可明确指定模式：
- **检查（Check）**：仅执行事实核查和语言润色
- **评估（Evaluate）**：仅提供建设性修改建议
- **全面审查（Full Review）**：两者兼顾（默认）

## 语言支持

- 中文稿件 → 中文回复
- 英文稿件 → 英文回复
- 自动识别，无需手动切换

## License

MIT
