# 中国出願人 B60C PCT国際公開ウォッチ

出願人の住所国が中国（CN）で、IPC `B60C`（車両用タイヤ）を含む PCT 国際公開（WO）を
毎週まとめ、GitHub Pages で公開するサイトです。
形式は michelin-wo-watch（タイヤ大手4社 PCT国際公開ウォッチ）と揃えています。

## 監視条件（2026-10-23 確定）

- 対象: WIPO PATENTSCOPE の PCT 国際公開のみ（毎週木曜公開）
- IPC: `B60C` を含む（全サブクラス、前方一致）
- 出願人: 住所国が `CN` の出願人を含む（筆頭出願人に限らない）
  - PATENTSCOPE 検索フィールド: `IC:B60C AND PAA:CN AND DP:YYYYMMDD`
  - 週次公開リスト（Browse by Week）でも照合し、筆頭以外に CN 出願人がいる共同出願の漏れを防ぐ
- 各件の収録内容:
  - 一覧表: WO番号 / 出願人 / 発明の名称（日本語 + 原題）/ X文献の有無 / X文献の出願人
  - カード: 日本語要約（どんな発明？ / 解決したい課題 / ポイント）、書誌事項
    （出願人、国際出願番号・日、優先権、IPC、発明者、公開言語）、
    ISR 引用文献表（X/Y/A 区分、文献番号、出願人・権利者、関連請求項、該当箇所）、
    PATENTSCOPE へのリンク

## 構成

```
index.html          トップ（週次レポート一覧）
weeks.json          週一覧の機械可読データ（新しい順）
assets/style.css    共通スタイル
weeks/YYYY-WW/      各週のレポート（index.html）
weeks/_template/    新しい週を作るためのテンプレート
```

## 週次更新手順

1. その週の PCT 公開日（木曜）で PATENTSCOPE を検索し、条件に合う WO を抽出する
2. 各件について PATENTSCOPE 詳細（patentscope2.wipo.int 経由）で書誌・要約・請求項・明細書・ISR を確認する
3. `weeks/_template/` を `weeks/YYYY-WW/` にコピーしてカードを作成する
4. トップの `index.html` の WEEKS-LIST 先頭に1行追加し、`weeks.json` の先頭にも追加する
5. commit / push すると GitHub Pages に反映される

## 注記

- PATENTSCOPE の通常ページはプログラムアクセスで CAPTCHA が出ることがあるため、詳細確認は公式ホスト patentscope2.wipo.int 経由で行う（CAPTCHA の解答・回避はしない）
- 見解書（ISA/237）の内容は分析対象外。ISR に記載された関連請求項の範囲だけを示す
