# ARREST GAME - Changelog

## v0.0.04 — 2026-10-07

### Refactoring

v0.0.03で動作していたARREST GAMEを、機能を増やさず内部構造を整理。

* 犯罪ごとの設定を `config/crimes.sk` に集約
* 犯罪のON/OFFを `enabled` で管理
* 逮捕処理を `core/crime.sk` に共通化
* 犯罪ファイルは「何をしたか」の判定に集中
* 牢屋処理を `core/jail.sk` に分離
* BossBar処理を `core/bossbar.sk` に分離
* 収監中のプレイヤー保護を `core/protection.sk` に分離
* メッセージ設定を `config/messages.sk` に集約
* サウンド処理用に `core/sound.sk` を追加

### Crime System

各犯罪から共通関数を呼び出す構造へ変更。

```text
crime/*.sk
    ↓
arrest_crime(player, "crime-id")
    ↓
core/crime.sk
    ↓
共通条件チェック
    ↓
config/crimes.sk から設定取得
    ↓
牢屋生成・収監
```

共通条件として以下を `core/crime.sk` で管理。

* ARREST GAMEがON
* 対象ワールド
* Survivalモード
* すでに収監中ではない
* 犯罪が `enabled`

### Crime Configuration

犯罪ごとに以下を設定可能。

* 犯罪名
* 収監時間
* 保釈アイテム
* 保釈個数
* 保釈表示名
* 犯罪のON/OFF

### Crimes

v0.0.04では以下の犯罪を管理。

* 暴行罪
* ボート無免許罪
* 窃盗罪
* たまご泥棒罪
* 花がかわいそう罪
* 草刈り無免許罪
* 火遊び危険罪
* サボり罪
* なんかかわいそう罪
* 凝視罪
* 銃刀法違反
* ポイ捨て罪

### Technical Core

v0.0.04の技術的な中心は、**犯罪判定と逮捕処理の分離**。

```text
犯罪ファイル
  = 犯罪を検知する

core/crime.sk
  = 逮捕条件を確認する

config/crimes.sk
  = 犯罪ごとの設定を持つ

core/jail.sk
  = 牢屋を管理する

core/bossbar.sk
  = BossBarを管理する

core/protection.sk
  = 収監中の保護を管理する
```

これにより、犯罪を追加・削除・無効化しても、共通の逮捕システムを変更せずに管理できる構造とした。

---

## v0.0.03 — 2026-10-02

### Added

* 基本的な犯罪判定
* 5×5牢屋
* 牢屋への収監
* 保釈システム
* 収監時間による自動釈放
* BossBar
* 収監中プレイヤー保護
* 牢屋破壊防止
* 花踏み罪
* サボり罪
* 不法投棄罪
* なんかかわいそう罪
* ボート無免許罪

### Improvements

* 犯罪ごとの収監時間を設定可能に
* 犯罪ごとの保釈条件を設定可能に
* 収監中の再逮捕を防止
* 犯罪処理を複数ファイルへ分割

---

## v0.0.02 — 2026-10-02

### Added

* 犯罪ごとの収監時間
* 犯罪ごとの保釈アイテム
* 犯罪ごとの保釈個数
* 保釈金表示
* 四方向の保釈看板
* BossBarによる残り時間表示
* 逮捕タイトル

---

## v0.0.01 — 2026-10-01

### Initial Prototype

* 犯罪検知
* 逮捕
* 5×5牢屋生成
* プレイヤー収監
* 鉄インゴットによる保釈
* 180秒による自動釈放

基本となる

```text
犯罪
 ↓
逮捕
 ↓
収監
 ↓
保釈 / 時間切れ
 ↓
釈放
```

のゲームループを構築。
