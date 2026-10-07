# ARREST GAME

Minecraft の世界で、日常的な行動を「犯罪」として判定し、犯罪者をその場で逮捕・収監するゲーム。

本作品は、**ドズル社の動画で扱われていた「やったら逮捕される世界」の企画・ゲーム性を再現することを目的として制作した個人制作作品**です。

> ※本リポジトリはゲームシステムを Minecraft + Paper + Skript で再現・実装するものであり、ドズル社および関係者による公式作品ではありません。

## 参考にした動画

## Overview

プレイヤーが特定の行動をすると犯罪として判定されます。

```text
プレイヤーの行動
      ↓
犯罪判定
      ↓
罪状決定
      ↓
逮捕
      ↓
牢屋生成・収監
      ↓
BossBarで刑期表示
      ↓
刑期終了 または 保釈
      ↓
解放
```

---

## Environment

* Minecraft: 26.2
* Paper: 26.2-112
* Skript: 2.16.1
* Java: 25

---

## Installation

### 1. Paperサーバーを起動

Paper26.2を使用したサーバーを用意します。

### 2. Skriptを導入

SkriptをPaperサーバーに導入します。

### 3. Skriptファイルを配置

本リポジトリの `skript/arrest/` 以下を、サーバーのSkriptフォルダに配置します。

```text
plugins/
└── Skript/
    └── scripts/
        └── arrest/
```

### 4. Skriptを読み込む

サーバーコンソールまたはゲーム内から、必要に応じてSkriptをリロードします。

```text
/sk reload scripts
```

個別のファイルをリロードする場合は、対象ファイルを指定してください。

---

## Basic Usage

ARREST GAMEの基本操作：

```text
/arrest on
/arrest off
/arrest status
```

### `/arrest on`

ARREST GAMEを開始します。

犯罪判定が有効になります。

### `/arrest off`

ARREST GAMEを停止します。

犯罪判定を無効にします。

### `/arrest status`

現在の稼働状態や対象ワールドなどを確認します。

---

## Main Features

### Arrest

* 犯罪行為を検知
* 罪状を表示
* プレイヤーを逮捕
* その場に牢屋を生成
* 収監時間を管理
* BossBarで刑期を表示
* 刑期終了時に解放

### Jail

* 5 × 5
* 高さ5
* reinforced_deepslateによる床・天井
* iron_barsによる壁
* 四方向に保釈看板
* 保釈システム
* 牢屋IDによる管理
* プレイヤーと牢屋の紐付け
* 牢屋の破壊防止

### Prisoner Protection

収監中のプレイヤーには以下の保護を行います。

* 無敵
* 耐性V
* 水中呼吸
* 火炎耐性
* 体力減少防止
* 満腹度減少防止
* 収監中は他の犯罪判定を行わない

---

## Test Environment

基本的には、専用のARREST GAME用ワールドを用意してテストすることを推奨します。

Multiverse-Coreを使用している場合は、例えば以下のようにワールドを作成できます。

### ワールド作成

```text
/mv create arrest
```

### ARRESTワールドへ移動

```text
/mvtp arrest
```

参加者全員をARREST GAME用ワールドへ移動させます。

### Skriptをリロード

スクリプトを変更した場合は、必要に応じてリロードします。

```text
/sk reload scripts
```

### ARREST GAMEを開始

```text
/arrest on
```

これでARREST GAMEを開始できます。

---

## Recommended Server Settings

`server.properties` で以下の設定を推奨します。

```properties
view-distance=8
simulation-distance=6
```

* `view-distance=8`
  * プレイヤーから見えるチャンクの距離
* `simulation-distance=6`
  * モブやレッドストーンなど、実際に処理されるチャンクの距離

ARREST GAMEでは、5～10人程度でのプレイを想定しています。

必要以上に描画・シミュレーション範囲を広げず、サーバー負荷とのバランスを取る設定です。

