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

### 公開前に残っていること（2026-10-03 更新）

- 予約フォームの受け皿：GAS を設置して `/exec` のURLをもらえば `CONFIG.formEndpoint` に設定する。通知先はスクリプトを設置したアカウントに自動で届くので、コードの編集は不要
- 休診日・年末年始（`CONFIG.holidays`）、`og:url` / `og:image`、`privacy.html` と法人ポリシーの整合

### 解決済み（2026-10-03）

- 分割払い：最大回数は載せない。「月々19,000円台〜」は手術費用のみを分割した場合の目安と明記（[[2026-10-03-meieki-lp-prelaunch]]）
- 治療期間・回数：手術1回、歯の装着まで約3〜6か月、通院5〜7回（FAQ とリスク欄に記載）
- 実績数値：2023年のまま掲載可（集計期間を併記済み。公開中のLPも2023年）。新しい集計があれば差し替え
- 医師3名の写真の掲載：了承済み
- 作業ブランチ `claude/youthful-wozniak-5voo5e`（デフォルトブランチには未マージ）

### メモ

- 医院が確定させた内容は `claude/lucid-hawking-qc6d1a` の `single-page-lp/README.md`「修正履歴」にある（2026-10-02 の赤ペン修正）。同じ医院の別LPなので、事実確認はまずここを見る

## ほかのブランチ（未マージ。詳細は各ブランチの README）

| ブランチ | 中身 | 最終更新 |
| --- | --- | --- |
| `claude/lucid-hawking-qc6d1a` | 1ファイル版オールオン4 LP（all_on_4_007 用、v6）、名駅LPの赤ペン修正 | 2026-10-02 |
| `claude/bold-johnson-q053s3` | アルティメイト栄歯科・矯正歯科 インプラントLPのデザイン改修版 | 2026-10-03 |
| `claude/nice-curie-poj2qx` | いびきコンテンツ事業「となりのいびき相談室」（LINE 7日間ステップ・LP・ショート動画台本30本）。医療法人とは別事業 | 2026-10-02 |
| `claude/upbeat-davinci-ltj2fj` | Claude Code スキル `/text-to-slide`（YouTube台本から Gemini でスライド画像を生成） | 2026-10-03 |
