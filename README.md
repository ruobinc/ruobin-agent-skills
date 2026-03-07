# ruobin-agent-skills

Agentスキル

## スキル一覧

| スキル                                            | 概要                                                                             |
| ------------------------------------------------- | -------------------------------------------------------------------------------- |
| [slack-tableau-analysis](slack-tableau-analysis/) | Slack会話から仮説を生成し、Tableauデータで検証、Canvasで共有する分析ワークフロー |

## インストール方法

1. 使いたいスキルのフォルダをZip化する（例: `slack-tableau-analysis.zip`）
2. Claude Desktopを開く
3. **Settings > Capabilities > Skills >Go to Customize** に移動
4. Zipファイルをアップロード

## slack-tableau-analysis

Slack会話から仮説を生成し、Tableauデータで検証、Web情報で補強した分析レポートをSlack Canvasとして共有する。

### 必要MCP

- **Slack MCP Server** - [セットアップガイド](https://docs.slack.dev/ai/slack-mcp-server)
- **Tableau MCP Server** - [セットアップガイド](https://tableau.github.io/tableau-mcp/docs/intro)

### ワークフロー

1. **Slack情報収集** - 関連するSlack会話を検索し、3-5個の仮説を生成
2. **仮説選択** - ユーザーが検証する仮説を選択
3. **データ構造確認** - Tableau MCPでデータソース・フィールドを探索
4. **データ分析** - 仮説検証に必要なデータを取得・分析
5. **Index付与** - 各ファクトに情報源（`[S1]`, `[T1]`, `[W1]`）を紐付け
6. **Web補強** - 業界トレンド・外部要因を検索（必要時のみ）
7. **レポート報告** - 構造化された分析レポートをユーザーに提示
8. **Slack共有** - 承認後、Canvasを作成しチャンネルに共有
