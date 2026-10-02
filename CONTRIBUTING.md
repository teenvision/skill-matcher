# 贡献指南

感谢你愿意参与 `skill-matcher`。这份指南帮你用最少的时间做出被接受的改动。

## 提交前先聊一句（推荐）

对于**新增功能、改行为规则、调整目录结构**这类改动，建议先开一个 Issue 说明动机，
避免你写完 PR 才发现方向不对。

错别字、文档补全、样式微调这类小改动，直接提 PR 即可。

## 开发流程

1. **Fork** 本仓库，然后克隆你的 fork：

   ```bash
   git clone git@github.com:<你的用户名>/skill-matcher.git
   cd skill-matcher
   ```

2. 建一个说明用途的分支（不要直接改 `main`）：

   ```bash
   git switch -c fix/matching-edge-case
   ```

3. 修改、自测。

4. 提交时写清"改了什么、为什么"：

   ```bash
   git add <文件>
   git commit -m "fix: 修复中等候选被误判为跳过的问题"
   ```

5. 推送到你的 fork，然后向上游开 Pull Request。

## 提交信息规范

采用 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/) 风格：

| 前缀 | 用途 |
|---|---|
| `feat:` | 新增功能 |
| `fix:` | 修复问题 |
| `docs:` | 仅文档改动 |
| `chore:` | 杂项（配置、依赖、格式） |
| `refactor:` | 重构，不改变行为 |

示例：`docs: 补充 Windows 安装说明`

## 格式约定

仓库已配置 `.editorconfig` 与 `.gitattributes`：

- 一律使用 **UTF-8** 编码、**LF** 换行
- 文件末尾保留一个空行
- Markdown / YAML 使用 2 空格缩进

多数编辑器会自动读取 `.editorconfig`，无需手动设置。

## 修改技能本体时

`skill-matcher/SKILL.md` 是技能的行为定义，改动它等于改动运行时行为。请一并：

1. 在 `skill-matcher/references/matching-examples.md` 补 1–2 条对应的判定样例；
2. 在 PR 描述里说明"什么样的输入，期望什么样的输出"。

## 许可证

本项目采用 **Apache License 2.0**。你提交的贡献将同样以该许可证授权。
提交即表示你同意这一点，且确认你有权提交这些内容。

## 行为准则

参与本项目即表示你同意遵守 [行为准则](./CODE_OF_CONDUCT.md)。
