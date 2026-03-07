# Tableau MCP Tools Reference

## データソース探索

### list-datasources
- サイト内の公開データソース一覧を取得
- 最初にどんなデータがあるか把握するために使う

### get-datasource-metadata
- データソースのフィールドメタデータ（列名、型、説明）を取得
- 仮説検証に使えるフィールドがあるか確認

### query-datasource
- VizQL Data Service APIでデータソースにクエリ実行
- フィルタ・集計・ソートを指定して必要なデータを取得
- 仮説検証の核となるツール

## ビュー・ワークブック

### list-workbooks
- ワークブック一覧を取得

### list-views
- ビュー一覧を取得
- 既存ダッシュボードの確認に使用

### get-view-data
- ビューのデータをCSV形式で取得
- 既存ダッシュボードのスナップショットデータ

### get-view-image
- ビューの画像を取得
- 視覚的な確認に使用

### get-workbook
- ワークブックの詳細情報を取得

## 分析パターン

```
1. list-datasources → 利用可能なデータソース把握
2. get-datasource-metadata → 関連フィールド特定
3. query-datasource → 仮説検証データ取得
4. get-view-data → 既存ダッシュボードのデータ補完
```
