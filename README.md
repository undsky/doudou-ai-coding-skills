# doudou-ai-coding-skills

[doudou-ai-coding](https://gitee.com/undsky/doudou-ai-coding) 配套的 Agent Skills 仓库。

| 技能             | 作用                                                                     |
| ---------------- | ------------------------------------------------------------------------ |
| `doudou-any2ai`  | 音视频、文档、图片/PDF 转成 AI 友好文本                                  |
| `doudou-product` | 需求资料或参考项目链接转成 PRD、设计说明、数据库 SQL、研发说明、测试用例 |
| `doudou-test`    | 已获授权的 Web 应用黑盒/白盒测试，输出 Markdown 测试报告                 |

## 安装

```bash
npx skills add https://gitee.com/undsky/doudou-ai-coding-skills.git
```

## 各技能说明

技能不用手动调用，Agent 会按对话内容自动触发。下面每个技能的「使用示例」可以直接照着说。

### doudou-any2ai

三条链路共用一个后端服务实例。服务地址按 `--base` 参数 → 环境变量 `doudou_any2api_url` → 项目根 `.env` → 技能目录 `.env`（默认 `http://localhost:5678`）的顺序查找，命中即停。改地址优先用前三种，别动技能自带的 `.env`，否则 git 会一直显示它被修改：

```bash
export doudou_any2api_url=http://192.168.1.10:5678
# 或在自己的项目根
echo 'doudou_any2api_url=http://192.168.1.10:5678' >> .env
```

脚本只用 Python 3 标准库，不需要装依赖，转换都在服务端跑。产物默认写到项目根 `resources/any2ai/`，文件名带时间戳。

#### 使用示例

```text
把 data/口播.mp4 转成中文字幕
data/会议录音.m4a 说了什么，我要纯文本，不用存文件
提取 docs/需求.docx 的内容
report/财报.xlsx 转成 Markdown 存到 out/
识别 screenshot.png 里的文字
scan.pdf 是扫描件，OCR 一下
data/ 目录下的文件都转成文本
```

音视频耗时约为时长的 0.7–1 倍（1 小时录音要等 45 分钟以上），上限 100MB。听得出语种就直接说，比让它自己检测快且准。不想留文件就说「不用存」，内容只留在对话里。

### doudou-product

交付物默认写到项目根 `resources/product/`。分析参考项目链接需要 chrome-devtools-mcp。

#### 使用示例

```text
按 docs/需求/ 里的资料做产品设计，数据库用 MySQL，表名字段名用英文
读 docs/需求说明.md，出一份 PRD 和数据库表结构，SQLite，命名用汉语拼音
分析 https://example.com/admin 这个后台，出参考项目分析报告
参考 https://example.com 的预约功能，结合 docs/需求/ 出完整设计，PostgreSQL
```

数据库类型（MySQL / PostgreSQL / SQLite）和命名规范（英文单词 / 汉语拼音）一开始就说清楚，能省掉两轮反问。完整设计出五份交付物：PRD、设计交付说明、数据库表结构 SQL、研发实现说明、测试验收用例，共用同一个时间戳。只给链接、只要分析报告时，它不会追问数据库。

新建业务表统一 `biz_` 前缀，统一带 `status`、`create_by`、`create_time`、`update_by`、`update_time`、`remark` 字段。

### doudou-test

测试报告默认写到项目根 `resources/test/`。浏览器测试需要 chrome-devtools-mcp。白盒分析按 doudou-ai-coding 的目录约定读源码（`doudou-vue3/`、`doudou-eggjs/`、`doudou-uniapp/`），用在别的项目上要告诉 Agent 实际目录。技能默认排除模版内置功能，只测新增业务功能。

#### 使用示例

```text
开始测试 http://localhost:80，黑盒，只读
测试 http://localhost:80 的订单模块，黑白盒都要，测试环境，允许增删改
http://localhost:80 白盒测一遍，源码在 doudou-vue3/ 和 doudou-eggjs/
测 http://192.168.1.10 的预约功能，账号 test/test123，不要动数据
```

先选黑盒 / 白盒 / 两者，再确认是否允许增删改，默认只读。生产环境默认不做真实写操作。开测前它会列出识别到的业务模块让你确认，只有模版内置功能时会直接说没有可测范围。有测试账号就一起给，没有账号只能测到登录前的页面。

## 开源协议

[MIT](LICENSE)
