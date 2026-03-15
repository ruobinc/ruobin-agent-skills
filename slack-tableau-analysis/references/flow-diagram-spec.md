# 分析フロー図の生成仕様

`visualize:show_widget` ツール（Visualizer）を使い、SVG形式でStep 1〜7の分析フローを図示する（Step 8のCanvas共有は含めない）。

## フロー図の構成ルール

Step 1〜7を上から下へノードとして配置する:

```
[Step 1: Slack情報収集] ← パープル色（Slack）
    ↓ (Slackチャンネルごとのサブノード)
[Step 2: ユーザーに仮説提示・選択] ← アンバー色（ユーザーアクション）
    ↓
[Step 3: Tableauデータ構造の確認] ← ティール色（Tableau）
    ↓
[Step 4: Tableauデータ取得・分析] ← ティール色（Tableau）
    ↓ (取得した分析軸ごとのサブノード)
[Step 5: Web情報による補強] ← 条件付き
    ↓
[Step 6: データソースIndex付与]
    ↓
[Step 7: 分析レポート作成・報告 → フロー図表示] ← コーラル色（分析結果）
```

## 色の割り当て

| 色         | 対象                                   |
| ---------- | -------------------------------------- |
| `c-purple` | Slack関連ノード・ワークフロー起点/終点 |
| `c-teal`   | Tableauデータ関連ノード                |
| `c-amber`  | ユーザーアクション（選択・確認）ノード |
| `c-coral`  | 分析結果・レポートノード               |
| `c-gray`   | Slackチャンネル等のサブノード          |

## 実装のポイント

- viewBox: `"0 0 680 [H]"` — コンテンツ量に合わせてHを調整（目安: ノード数 × 80px + 余白）
- メインノード: 幅240px、高さ44px（1行）または56px（2行）
- サブノード: 幅130px、高さ44px、横並びで扇状に配置
- 矢印: `class="arr" marker-end="url(#arrow)"` を使用
- サブノードへの矢印は細め（`stroke-width="1"`）で扇状に引く
- すべてのテキストに `dominant-baseline="central"` を指定
- `<defs>` に arrowマーカーを必ず含める

## SVGフロー図の出力例（骨格）

```svg
<svg width="100%" viewBox="0 0 680 780">
  <defs>
    <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5"
            markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"
            stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
    </marker>
  </defs>

  <!-- Step 1: Slack情報収集 -->
  <g class="c-purple">
    <rect x="220" y="20" width="240" height="44" rx="8" stroke-width="0.5"/>
    <text class="th" x="340" y="42" text-anchor="middle"
          dominant-baseline="central">Slack情報収集</text>
  </g>

  <!-- Slackチャンネル サブノード（c-gray、横並び） -->
  <!-- ... -->

  <!-- Step 2: 仮説生成 -->
  <!-- ... -->

  <!-- 以降のステップを同様に配置 -->
</svg>
```
