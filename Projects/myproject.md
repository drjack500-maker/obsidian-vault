---
date: 2026-10-03
tags: [project, lp, dental, google-ads, line]
project: myproject
related: []
---

# myproject

GitHub: `drjack500-maker/myproject`（**public**。患者情報や秘匿情報は入れない）
歯科医院の集患用LP・広告まわりの制作物をまとめたリポジトリ。案件ごとにブランチが分かれている。

## メイン: 名駅歯科クリニック・矯正歯科 オールオン4 LP

- デフォルトブランチ `claude/lp-conversion-improvement-ui40f5`（最終更新 2026-09-30）
- 目的: 現LP https://www.meieki-dental.net/all_on_4_004/ の予約を増やす

### できているもの

- 改善版LP `lp/`：静的ファイルでビルド不要。広告キーワード別に見出しを5パターン出し分け（`?v=` または `utm_term`）
- 予約フォーム（LP内の3ステップ）と受信用の Google Apps Script（予約台帳・通知メール）
- 現LPの応急処置版 `current-lp-hotfix/`：医療広告ガイドライン上リスクのある表現など29か所を修正
- 資料 `docs/`：現LPの診断レポート、改善提案書、Google広告の広告文（CSV付き）、計測手順（GTM `GTM-TKQ2RFV`）、受付マニュアル
- テスト `npm test`：HTML検証、受信スクリプト10件、ブラウザ操作20件、アクセシビリティ検査

### 公開前に残っていること

- `CONFIG.formEndpoint` 未設定（GASをデプロイしてURLを設定。未設定だと本番では電話案内になる）
- GAS の通知メールの送信先
- 分割払いの最大回数（「最大120回」は外部サイトの情報で未確認）
- 実績数値が2023年のまま
- 休診日・年末年始、`og:url` / `og:image`、`privacy.html` と法人ポリシーの整合、医師写真の掲載了承

## ほかのブランチ（未マージ。詳細は各ブランチの README）

| ブランチ | 中身 | 最終更新 |
| --- | --- | --- |
| `claude/lucid-hawking-qc6d1a` | 1ファイル版オールオン4 LP（all_on_4_007 用、v6）、名駅LPの赤ペン修正 | 2026-10-02 |
| `claude/bold-johnson-q053s3` | アルティメイト栄歯科・矯正歯科 インプラントLPのデザイン改修版 | 2026-10-03 |
| `claude/nice-curie-poj2qx` | いびきコンテンツ事業「となりのいびき相談室」（LINE 7日間ステップ・LP・ショート動画台本30本）。医療法人とは別事業 | 2026-10-02 |
| `claude/upbeat-davinci-ltj2fj` | Claude Code スキル `/text-to-slide`（YouTube台本から Gemini でスライド画像を生成） | 2026-10-03 |
