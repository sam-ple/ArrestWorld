# ARREST GAME

* * *

Minecraft の世界で、日常的な行動を「犯罪」として判定し、犯罪者をその場で逮捕・収監するゲーム。

本作品は、**ドズル社の動画で公開された「〇〇したら逮捕される世界」の企画・ゲーム内容を参考に、Minecraft + Paper + Skript を用いて個人で実装・再現したファンメイド作品です。**

本作品はドズル社および関係者による公式作品ではなく、**ドズル社との関係・提携・公認を示すものではありません。**

> ドズル社二次創作ガイドライン  
> https://www.dozle.jp/support_rule/#support_fanworks

## 参考にした動画

* 【理不尽すぎる】〇〇すると逮捕される世界でエンドラ討伐！【マイクラ】(2026/09/26)
  * https://www.youtube.com/watch?v=9PIAa67Rx4M
* エンドラ討伐してたら逮捕されました【マイクラ】(2025/08/08)
  * https://www.youtube.com/watch?v=CZ4jDD7V0vc
* 【マイクラ】〇〇したら逮捕される世界でサバイバル(2022/11/15)
  * https://www.youtube.com/watch?v=SnFePUO4kD4

> 補足：発案者のみのまさん（ドズル社企画会議で視聴者のみのまさんのアイデアを元に動画化。）  
> https://www.youtube.com/watch?v=q15Fqy76T7M&t=521s  
> https://www.youtube.com/watch?v=h49ilAHtk_c&t=1814s  

* 本作品の制作にあたり、ドズル社の動画で公開されている「〇〇したら逮捕される世界」の企画・ゲーム内容を参考にしています。
* 本リポジトリでは、これらの動画で公開されたゲーム内容を参考に、Minecraft上で動作するゲームシステムとして独自に実装しています。  

---

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

## Installation

### 1. Paperサーバーを起動

Paper 26.2を使用したサーバーを用意します。

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

## Test Setup

基本的には、専用のARREST GAME用ワールドを用意してテストすることを推奨します。

Multiverse-Coreを使用している場合：

### ワールド作成

```text
/mv create arrest normal
```

### ARRESTワールドへ移動

```text
/mvtp arrest
```

### Skriptをリロード

スクリプトを変更した場合は、必要に応じてリロードします。

```text
/sk reload scripts
```

### ARREST GAMEを開始

```text
/arrest on
```

---

## Test Environment

本作品は、以下の環境で動作確認を行っています。

### Server

* OS: macOS
* Minecraft: 26.2
* Paper: 26.2-121
  * paper-26.2-121.jarでの実施
  * 10/7現在の最新版はpaper-26.2-132.jar
* Java: OpenJDK 25
* Skript: 2.16.1
  * Skript-2.16.1.jarでの実施
  * 10/7現在の最新はSkript-2.16.2.jar
* Players: 5～10人程度を想定

### Server Startup

6GBを割り当ててPaperサーバーを起動します。

```bash
java -Xms6G -Xmx6G -jar paper-26.2-121.jar nogui
```

### Network

外部からの接続にはplayitを使用しています。

* playit: Premium

サーバー起動後、playitのトンネルを起動して外部から接続できる構成でテストしています。

### Server Settings

```properties
view-distance=8
simulation-distance=6
```

* `view-distance=8`
  * プレイヤーから見えるチャンクの距離
* `simulation-distance=6`
  * モブやレッドストーンなどが実際に処理される範囲

5～10人程度でのプレイを想定し、描画・シミュレーション範囲とサーバー負荷のバランスを取った設定です。
