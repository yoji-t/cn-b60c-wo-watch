# B60C PCT国際公開ウォッチ（ブリヂストン除く）

ブリヂストン関連の出願人を除き、IPC `B60C`（車両用タイヤ）を含む PCT 国際公開（WO）を
毎週まとめ、GitHub Pages で公開するサイトです。
形式は michelin-wo-watch（タイヤ大手4社 PCT国際公開ウォッチ）と揃えています。

※2026年第43週以前は旧条件（出願人の住所国が中国）で作成したレポートです。
新条件は2026年第44週（2026-10-29公開分）から適用します。リポジトリ名・URLは従来のままです。

## 監視条件（2026-10-23 変更確定）

- 対象: WIPO PATENTSCOPE の PCT 国際公開のみ（毎週木曜公開）
- IPC: `B60C` を含む（全サブクラス、前方一致）
- 出願人: 限定しない。ただし、出願人（筆頭に限らない）にブリヂストン関連を含む案件は除外する
  - 除外対象の例: BRIDGESTONE CORPORATION（株式会社ブリヂストン）、BRIDGESTONE EUROPE NV/SA、Bridgestone Americas Tire Operations, LLC、BRIDGESTONE BANDAG, LLC、その他名称に BRIDGESTONE／ブリヂストンを含む出願人
  - 共同出願でブリヂストン関連が含まれる案件も除外する
  - PATENTSCOPE 検索: `DP:[DD.MM.YYYY TO DD.MM.YYYY] AND IC:B60C`（日付は DD.MM.YYYY 範囲指定、その週の木曜）で全件を抽出し、各件の出願人を確認して除外を判定する
  - 週次公開リスト（Browse by Week）でも照合し、共同出願の漏れを防ぐ
  - 件数の目安: 週平均 約35件（全体）→ ブリヂストン関連を除くと週平均 約30件（2026-09-17〜10-22の6週で全体209件・ブリヂストン関連30件）
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

1. その週の PCT 公開日（木曜）で PATENTSCOPE を検索し、B60C を含む WO を全件抽出する
2. 各件の出願人を確認し、ブリヂストン関連を含む案件を除外する
3. 残った各件について PATENTSCOPE 詳細（patentscope2.wipo.int 経由）で書誌・要約・請求項・明細書・ISR を確認する
4. `weeks/_template/` を `weeks/YYYY-WW/` にコピーしてカードを作成する
5. トップの `index.html` の WEEKS-LIST 先頭に1行追加し、`weeks.json` の先頭にも追加する
6. commit / push すると GitHub Pages に反映される

## 注記

- PATENTSCOPE の通常ページはプログラムアクセスで CAPTCHA が出ることがあるため、詳細確認は公式ホスト patentscope2.wipo.int 経由で行う（CAPTCHA の解答・回避はしない）
- 見解書（ISA/237）の内容は分析対象外。ISR に記載された関連請求項の範囲だけを示す
