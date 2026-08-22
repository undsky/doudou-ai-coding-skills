# doudou-ai-coding-skills

[doudou-ai-coding](https://gitee.com/undsky/doudou-ai-coding) 配套的 Agent Skills 仓库，用 [skills](https://github.com/vercel-labs/skills) CLI 分发，支持 Claude Code、Codex、Cursor、iFlow、Qwen Code 等 70+ Agent。

| 技能             | 作用                                                                            |
| ---------------- | ------------------------------------------------------------------------------- |
| `doudou-any2ai`  | 音视频、文档、图片/PDF 转成 AI 友好文本：whisper 听录、anydoc 转 Markdown、PaddleOCR 识别 |
| `doudou-product` | 需求资料或参考项目链接转成 PRD、设计说明、数据库 SQL、研发说明、测试用例         |
| `doudou-test`    | 已获授权的 Web 应用黑盒/白盒测试，输出 Markdown 测试报告                        |

## 安装

装全部技能，交互选择目标 Agent：

```bash
npx skills add https://gitee.com/undsky/doudou-ai-coding-skills.git
```

用 `--skill` 只装指定的，参数可重复传：

```bash
npx skills add https://gitee.com/undsky/doudou-ai-coding-skills.git --skill doudou-any2ai
npx skills add https://gitee.com/undsky/doudou-ai-coding-skills.git --skill doudou-product --skill doudou-test
```

> Gitee 地址要带 `.git` 后缀。不带后缀会被 CLI 当成 well-known 接口去发现技能，拿不到东西就失败了。

装之前先看仓库里有什么：

```bash
npx skills add https://gitee.com/undsky/doudou-ai-coding-skills.git --list
```

### 常用参数

| 参数                      | 说明                                                            |
| ------------------------- | --------------------------------------------------------------- |
| `-s, --skill <names...>`  | 只装指定技能，`'*'` 表示全部                                    |
| `-a, --agent <agents...>` | 指定 Agent，如 `claude-code`、`codex`、`iflow-cli`，`'*'` 表示全部 |
| `-l, --list`              | 只列技能不安装                                                  |
| `-g, --global`            | 装到用户目录而不是当前项目                                      |
| `--copy`                  | 复制文件而不是软链到各 Agent 目录                               |
| `-y, --yes`               | 跳过所有确认，适合 CI                                           |
| `--all`                   | 全部技能装到全部 Agent，不问                                    |

非交互安装到指定 Agent：

```bash
npx skills add https://gitee.com/undsky/doudou-ai-coding-skills.git \
  --skill doudou-any2ai -a claude-code -y
```

### 安装位置

默认装到当前项目，按 Agent 各自的约定目录放：Claude Code 是 `.claude/skills/`，Codex 是 `.agents/skills/`。选多个 Agent 时 CLI 会在 `.agents/skills/` 留一份，其余目录软链过去。加 `-g` 则装到 `~/.claude/skills/` 这类用户目录。

项目级安装会在项目根生成 `skills-lock.json`，记录来源和内容哈希，提交进版本库队友就能拿到同一份技能。

### 更新与卸载

```bash
npx skills update                      # 更新全部
npx skills update doudou-any2ai        # 更新单个
npx skills list                        # 看已装的
npx skills remove doudou-test          # 卸载
```

### 不安装直接用

```bash
npx skills use https://gitee.com/undsky/doudou-ai-coding-skills.git@doudou-product | claude
```

## 仓库结构

```text
skills/
├── doudou-any2ai/
│   ├── SKILL.md
│   ├── .env              # 后端服务地址默认值，随仓库分发
│   └── scripts/
│       ├── whisper.py    # 音视频转字幕
│       ├── anydoc.py     # 文档转 Markdown
│       └── paddleocr.py  # 图片/PDF OCR
├── doudou-product/
│   └── SKILL.md
└── doudou-test/
    └── SKILL.md
```

一个技能一个目录，目录里必须有 `SKILL.md`，frontmatter 的 `name` 和 `description` 决定 CLI 列表和 Agent 何时触发。CLI 从 `skills/` 自动发现，新增技能建目录即可，不用改配置。

## 各技能说明

### doudou-any2ai

三条链路共用一个后端服务实例。服务地址按 `--base` 参数 → 环境变量 `doudou_any2api_url` → 项目根 `.env` → 技能目录 `.env`（默认 `http://localhost:5678`）的顺序查找，命中即停。改地址优先用前三种，别动技能自带的 `.env`，否则 git 会一直显示它被修改：

```bash
export doudou_any2api_url=http://192.168.1.10:5678
# 或在自己的项目根
echo 'doudou_any2api_url=http://192.168.1.10:5678' >> .env
```

脚本只用 Python 3 标准库，不需要装依赖，转换都在服务端跑。产物默认写到项目根 `resources/any2ai/`，文件名带时间戳。

### doudou-product

交付物默认写到项目根 `resources/product/`。分析参考项目链接需要 chrome-devtools-mcp。

### doudou-test

测试报告默认写到项目根 `resources/test/`。浏览器测试需要 chrome-devtools-mcp。白盒分析按 doudou-ai-coding 的目录约定读源码（`doudou-vue3/`、`doudou-eggjs/`、`doudou-uniapp/`），用在别的项目上要告诉 Agent 实际目录。技能默认排除模版内置功能，只测新增业务功能。

## 开源协议

[MIT](LICENSE)
