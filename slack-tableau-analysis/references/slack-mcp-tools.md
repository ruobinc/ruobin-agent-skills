# Slack MCP Tools Reference

## 情報収集ツール

### slack_search_public_and_private
- Slack内のメッセージ・ファイルを検索
- `query`: 検索クエリ（Slack検索構文対応: `from:user`, `in:channel`, `after:2025-01-01`等）
- 仮説生成フェーズで最初に使うツール

### slack_read_channel
- チャンネルの最新メッセージ履歴を取得
- `channel_name`: チャンネル名
- `limit`: 取得件数（デフォルト100）

### slack_read_thread
- スレッドの全メッセージを取得
- `channel_id` + `thread_ts`: スレッド特定

### slack_search_channels
- チャンネル名・説明で検索
- 関連チャンネルの発見に使用

### slack_search_users
- ユーザー名・メールで検索

### slack_read_user_profile
- ユーザープロフィール詳細

## 出力ツール

### slack_create_canvas
- Markdown形式のCanvasを作成
- `title`: Canvas タイトル
- `channel_id`: 共有先チャンネル
- `content`: Markdown本文
- 分析レポートの最終出力に使用

### slack_send_message
- チャンネルにメッセージ送信
- `channel_id`: 送信先
- `text`: メッセージ本文

## 検索クエリの書き方

```
# 特定チャンネル内の売上関連
in:sales-all 売上 減少

# 特定ユーザーの発言
from:tanaka 予算

# 日付範囲指定
after:2025-01-01 before:2025-03-01 KPI

# 複合検索
in:sales-all from:tanaka 売上 after:2025-02-01
```
