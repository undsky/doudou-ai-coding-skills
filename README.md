# doudou-ai-coding-skills

[doudou-ai-coding](https://gitee.com/undsky/doudou-ai-coding) 配套的 Agent Skills 仓库。

| 技能             | 用途                                                                                                 |
| ---------------- | ---------------------------------------------------------------------------------------------------- |
| `doudou-any2ai`  | 将任意类型文件 转成 AI 友好文本                                                                      |
| `doudou-product` | 根据需求资料或参考项目链接，输出产品需求文档、设计交付说明、数据库表结构、研发实现说明、测试验收用例 |
| `doudou-test`    | 已获授权的 Web 应用黑盒/白盒测试，输出 Markdown 测试报告                                             |

## 安装

```bash
npx skills add undsky/doudou-ai-coding-skills
```

## 使用

### doudou-any2ai

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
