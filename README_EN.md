<h1 align="center">doudou-ai-coding-skills</h1>

<p align="center">
  <a href="README.md">简体中文</a> | <b>English</b>
</p>

<p align="center">
  Companion Agent Skills repository for <a href="https://github.com/undsky/doudou-ai-coding">doudou-ai-coding</a>.<br>
  Provides full-lifecycle AI coding assistance across product requirement analysis, prototyping, database design, development, testing, and deployment.
</p>

<p align="center">
  <img src="./assets/cover.png" alt="doudou-ai-coding-skills Banner" width="100%" />
</p>

---

## 📑 Table of Contents

- [📦 Skills Overview](#-skills-overview)
- [📥 Installation](#-installation)
- [📖 Usage Guide](#-usage-guide)
  - [doudou-product (Product)](#doudou-product-product)
  - [doudou-dev (Development)](#doudou-dev-development)
  - [doudou-test (Testing)](#doudou-test-testing)
- [💬 Community & Discussion](#-community--discussion)
- [📄 License](#-license)

---

## 📦 Skills Overview

| Skill | Purpose |
| --- | --- |
| `doudou-dev` | Development debugging (`dev`) and production building (`build`) for frontend, backend, and mobile (`doudou-eggjs`, `doudou-vue3`, `doudou-uniapp`) |
| `doudou-product` | Generates PRDs, design delivery specifications, database schemas, development implementation guides, and test acceptance test cases from requirements or reference links |
| `doudou-test` | Authorized black-box / white-box testing for web applications, generating Markdown test reports |

---

## 📥 Installation

This project provides full-lifecycle AI coding support (for Antigravity, Claude Code, OpenCode, and other platforms) for https://github.com/undsky/doudou-ai-coding.

```bash
npx skills add undsky/doudou-ai-coding-skills --yes
```

---

## 📖 Usage Guide

### doudou-product (Product)

```
/doudou-product
```

Works in conjunction with **[doudou-llm-wiki-skill](https://github.com/undsky/doudou-llm-wiki-skill)** to generate product requirement documents (PRD), design delivery specifications, database table schemas, development implementation guides, and test acceptance test cases.

### doudou-dev (Development)

- **Development & Debugging**:
  ```
  /doudou-dev
  ```
  Keywords: "Start project", "Debug backend", "Run frontend"
- **Production Build**:
  ```
  /doudou-dev build
  ```
  Keywords: "Build project", "Build frontend and backend", "Generate production bundle"

### doudou-test (Testing)

- **Web Admin Portal (`doudou-vue3`)**:
  ```
  /doudou-test http://localhost:8001
  ```
  Keywords: "Test frontend", "Test admin portal", "Test web UI"
- **Backend Service & API (`doudou-eggjs`)**:
  ```
  /doudou-test http://localhost:7001
  ```
  Keywords: "Test backend", "Test interface", "Test API"
- **Mobile Client (`doudou-uniapp`)**:
  ```
  /doudou-test http://localhost:9090
  ```
  Keywords: "Test mobile app", "Test H5"

---

## 💬 Community & Discussion

| WeChat Official Account | QQ Group (1095058701) |
| --- | --- |
| ![Official Account](https://cdn.undsky.com/img/gh.jpg) | ![QQ Group](https://cdn.undsky.com/img/qqqun.jpg) |

---

## 📄 License

This project is licensed under [CC BY-NC 4.0](LICENSE).

- Free for personal use, learning, research, and non-commercial projects.
- Please attribute the source when publishing derivative works publicly.
- Commercial use requires separate authorization; please contact the author.
