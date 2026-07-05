# GitHub Actions Claude Code

GitHub IssueやPull Requestに`@claude`とメンションするだけで、ClaudeがコードのレビューやIssueの実装を自動で行うリポジトリです。

## 使い方

IssueやPRのコメントに`@claude`とメンションして指示を書くと、Claudeが自動的にタスクを実行します。

### 例

```
@claude このバグを修正してください
@claude このIssueを実装してください
@claude このコードをレビューしてください
```

## セットアップ

### 必要なSecrets

| Secret名 | 説明 |
|---|---|
| `CLAUDE_CODE_OAUTH_TOKEN` | Claude Code の OAuthトークン |

Secretsは `Settings > Secrets and variables > Actions` から設定してください。

## トリガー

| イベント | 条件 |
|---|---|
| `issue_comment` | コメントに`@claude`が含まれる場合 |
| `pull_request_review_comment` | レビューコメントに`@claude`が含まれる場合 |
| `pull_request_review` | レビュー本文に`@claude`が含まれる場合 |
| `issues` | Issue本文またはタイトルに`@claude`が含まれる場合 |

## 使用技術

- [Claude Code Action](https://github.com/anthropics/claude-code-action)
- GitHub Actions
