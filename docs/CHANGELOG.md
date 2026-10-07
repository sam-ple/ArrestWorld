# ARREST GAME - Changelog

## v0.0.04c - 2026-10-07

### Repository / Documentation

* README.mdを整理
* `docs/` を必要最小限に整理
* 不要なドキュメントを削除
* `docs/TEST.md`、`docs/CHANGELOG.md` を残して管理
* 犯罪ファイルのコメント・記述方法を整理
* リポジトリ全体を完成版として整理

---

## v0.0.04b - 2026-10-07

### Repository

* README.mdを追加
* `docs/` を追加
* `skript/` を正式なコード格納場所として整理
* LICENSEを追加
* Gitによるバージョン管理を開始

### Note

v0.0.04bは、完成したARREST GAMEをリポジトリとして整理・保存するためのバージョン。

---

## v0.0.04a - 2026-10-06

### Final Adjustment

* 犯罪判定・逮捕処理を調整
* 牢屋・BossBar・保釈を含む一連のゲームフローを確認
* 効果音・演出を調整
* 各犯罪の動作を確認

---

## v0.0.04 - 2026-10-06

### Architecture

* `config / core / crime` に処理を分離
* 犯罪ごとの処理を個別ファイル化
* 共通処理を整理
* 牢屋・BossBar・犯罪判定の構成を整理

### Crimes

* 花踏み
* 環境破壊
* サボり
* 不法投棄
* ボート無免許
* なんかかわいそう
* その他の犯罪判定を追加・調整

---

## v0.0.03 - 2026-10-05

### Game Control

* `/arrest on`
* `/arrest off`
* `/arrest status`
* 対象ワールド管理
* ARREST GAMEのON/OFF管理
* ゲーム状態の一元管理

---

## v0.0.02 - 2026-10-01

### Prisoner Protection

* 収監中のプレイヤーを保護
* 無敵・各種状態異常対策を追加
* 収監中の犯罪判定を除外

---

## v0.0.01 - 2026-10-01

### Initial Implementation

* 5×5の牢屋を実装
* 保釈システムを実装
* BossBarによる刑期表示を実装
* 収監・解放の基本システムを実装
* 環境破壊罪を実装

ARREST GAMEの基本となる逮捕・収監システムを構築。
