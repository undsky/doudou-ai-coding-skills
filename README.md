# doudou-ai-coding-skills

[doudou-ai-coding](https://gitee.com/undsky/doudou-ai-coding) 配套的 Agent Skills 仓库。

| 技能             | 用途                                                                                                 |
| ---------------- | ---------------------------------------------------------------------------------------------------- |
| `doudou-dev`     | 跨平台管理前后端（`doudou-eggjs` 与 `doudou-vue3`）的开发调试（`dev`）与生产打包（`build`）           |
| `doudou-any2ai`  | 将任意类型文件 转成 AI 友好文本（按类型分派到 `doudou-stt` / `doudou-doc` / `doudou-ocr`）           |
| `doudou-product` | 根据需求资料或参考项目链接，输出产品需求文档、设计交付说明、数据库表结构、研发实现说明、测试验收用例 |
| `doudou-test`    | 已获授权的 Web 应用黑盒/白盒测试，输出 Markdown 测试报告                                             |

## 安装

```bash
npx skills add undsky/doudou-ai-coding-skills
```

## 使用

### doudou-dev

跨平台（Windows、macOS、Linux）一键运行开发调试或生产打包：

- **开发调试**（启动 `doudou-eggjs: npm run dev` 与 `doudou-vue3: pnpm dev`）：
  ```
  /doudou-dev
  # 或关键词：“启动项目”、“调试后端”、“运行前端”
  ```
- **生产打包**（执行 `doudou-eggjs: npm run build` 与 `doudou-vue3: pnpm run build:prod`）：
  ```
  /doudou-dev build
  # 或关键词：“打包项目”、“构建前后端”、“生成生产包”
  ```

### doudou-any2ai

本技能只做分派，实际转换由三个独立技能完成，需要额外安装：

```bash
npx skills add undsky/doudou-stt-skill   # 音视频 → 字幕 / 逐字稿
npx skills add undsky/doudou-doc-skill   # 文档、电子书 → Markdown
npx skills add undsky/doudou-ocr-skill   # 图片、PDF → 文字（OCR）
```

服务地址与用户标识配在各自技能目录的 `.env` 里（`DOUDOU_STT_*` / `DOUDOU_DOC_*` / `DOUDOU_OCR_*`）

如果不指定文件或目录，默认读取项目根目录下的 `resources/data` 里的文件

如果不指定保存位置，默认将结果保存到项目根目录下 `resources/any2ai` 目录下

```
/doudou-any2ai
```

### doudou-product

如果不指定资料位置或参考项目链接，默认从项目根目录下 `resources/any2ai` 获取需求分析资料

如果不指定输出目录，默认将结果保存到项目根目录下 `resources/product` 目录下

```
/doudou-product
```

### doudou-test

如果不指定输出目录，默认将结果保存到项目根目录下的 `resources/test` 目录下

```
/doudou-test http://localhost:8001
```

| 公众号                                       | QQ群                                          |
| -------------------------------------------- | --------------------------------------------- |
| ![公众号](https://cdn.undsky.com/img/gh.jpg) | ![QQ群](https://cdn.undsky.com/img/qqqun.jpg) |
