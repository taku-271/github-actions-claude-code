# github-actions-claude-code

GitHub ActionsでClaude Codeを使用するためのリポジトリです。

## 概要

このリポジトリは、[anthropics/claude-code-action](https://github.com/anthropics/claude-code-action)を利用して、GitHubのIssueやPull RequestでClaudeをAIアシスタントとして活用するための設定を提供します。

`@claude` とメンションするだけで、コードレビュー・バグ修正・機能実装などをAIが自動で行います。

## 使い方

IssueやPull Requestのコメントで `@claude` をメンションすると、Claude Codeが自動的に応答・対応します。

### 使用例

```
@claude このコードをレビューしてください
@claude このIssueを実装してください
@claude バグの原因を調査してください
@claude テストを追加してください
@claude READMEを更新してください
```

### 対応イベント

| イベント | 条件 |
|---------|------|
| Issueへのコメント | `@claude` を含む場合 |
| PRへのコメント | `@claude` を含む場合、またはClaudeが作成したブランチ（`claude/*`）の場合 |
| PRレビューの送信 | `@claude` を含む場合、またはClaudeが作成したブランチの場合 |

## セットアップ

### 1. Secretsの設定

リポジトリの **Settings > Secrets and variables > Actions** にて、以下のいずれかを設定してください。

| Secret名 | 説明 |
|---------|------|
| `ANTHROPIC_API_KEY` | Anthropic ConsoleのAPIキー（APIキー認証の場合） |
| `CLAUDE_CODE_OAUTH_TOKEN` | OAuthトークン（Pro/Maxサブスクリプションの場合） |

OAuthトークンはローカルで以下のコマンドを実行して生成できます。

```bash
claude setup-token
```

### 2. ワークフローファイル

`.github/workflows/claude.yml` にGitHub Actionsのワークフローが定義されています。このファイルを自リポジトリにコピーすることで同様の機能を利用できます。

### 3. 権限の確認

ワークフローには以下の権限が必要です。

```yaml
permissions:
  contents: write
  pull-requests: write
  issues: write
  id-token: write
```

## 動作の仕組み

1. `@claude` を含むコメントがトリガーとなる
2. GitHub Actionsが起動し、Claude Codeアクションを実行
3. ClaudeがIssue/PRの内容を解析
4. 必要に応じてコードを変更し、新しいブランチ（`claude/issue-<番号>-<日付>`）を作成
5. 変更内容をコミット・プッシュし、PRの作成リンクをコメントで通知

## 使用技術

- [Claude Code](https://claude.ai/code) by Anthropic
- [claude-code-action](https://github.com/anthropics/claude-code-action)
- GitHub Actions

## ライセンス

MIT
