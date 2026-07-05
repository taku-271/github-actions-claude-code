# github-actions-claude-code

GitHub ActionsでClaude Codeを使用するためのリポジトリです。

## 概要

このリポジトリは、[anthropics/claude-code-action](https://github.com/anthropics/claude-code-action)を利用して、GitHubのIssueやPull RequestでClaudeをアシスタントとして活用するための設定を提供します。

## 使い方

IssueやPull Requestのコメントで `@claude` をメンションすると、Claude Codeが自動的に応答・対応します。

### 例

```
@claude このコードをレビューしてください
@claude このIssueを実装してください
@claude バグの原因を調査してください
```

## セットアップ

### 必要な設定

1. `CLAUDE_CODE_OAUTH_TOKEN` をリポジトリのSecretsに設定してください。

### ワークフロー

`.github/workflows/claude.yml` にGitHub Actionsのワークフローが定義されています。以下のイベントをトリガーとしてClaudeが動作します。

- Issue・PRへのコメント（`@claude` を含む場合）
- Issueのオープン・アサイン（`@claude` を含む場合）
- PRレビューの送信（`@claude` を含む場合）

## 使用技術

- [Claude Code](https://claude.ai/code) by Anthropic
- [claude-code-action](https://github.com/anthropics/claude-code-action)
- GitHub Actions
