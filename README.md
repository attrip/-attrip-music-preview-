# ATTRIP Music Preview

ATTRIP Music の公開テスト環境です。

このリポジトリは、`attrip.jp` 側の音楽制作機能と、将来的な ChatGPT App 化を検証するための軽量な公開プレビュー環境として作りました。

公開URL:

https://attrip.github.io/-attrip-music-preview-/

## このプロジェクトの目的

ブラウザ上で、音楽理論を「読む」のではなく「触る」ための作曲UIを作ることが目的です。

最終的には、以下のような流れを目指しています。

- キーとスケールを選ぶ
- ダイアトニックコードを直感的に弾く
- コード進行を作る
- ビートやベースと組み合わせる
- MIDIでLogic Proなどへ送る
- ChatGPTとの会話からコードや進行を生成する
- ChatGPT AppのWidgetとして使えるようにする

## ここまでの経緯

### 1. 既存のBEAT ROOMを起点にした

もともと `attrip/attripthema` には、ブラウザでビートを作る `BEAT ROOM` がありました。

既存機能には、

- HIPHOP / DUBSTEP / D&B
- BPM変更
- 32ステップのビート
- 録音
- WAV保存
- エフェクト
- パターン保存

などがあり、Web Audio APIでKick / Snare / Hat / Bassを鳴らす基盤がすでに存在していました。

そのため、新しい音楽ツールをゼロから作るのではなく、BEAT ROOMを将来的に `MUSIC ROOM` に発展させる方針にしました。

### 2. コード機能を追加

最初のPRでは、BEAT ROOMに以下を追加しました。

- KEY選択
- Major / Natural Minor
- 7つのダイアトニックコード
- コードを押すとブラウザ内で発音
- 選んだコード進行を表示

音楽ロジックはWordPressテンプレートに直接埋め込まず、`AttripMusicEngine` として分離しました。

これは、後でChatGPT AppのWidgetへ持ち出せるようにするためです。

### 3. コード生成のオクターブ問題を修正

レビュー中に、G# Majorなどでスケールがオクターブをまたぐと、MIDIノートが下のオクターブへ巻き戻る問題を発見しました。

表示用の音名と、実際の絶対音高を分離し、コードのMIDIノートが正しく上昇するように修正しました。

その後、最初のコード機能PRをmainへマージしました。

### 4. ChatGPT App化を前提に設計変更

次に、単なるattrip.jp内の機能ではなく、ChatGPTの中でも使える音楽アプリとして考える方針に切り替えました。

目標は、

- ChatGPTで「暗めのJungleコード進行を作って」と指示
- Widget上にコード進行が表示
- その場で鳴らす
- 後からMIDIやLogic Proへ送る

という体験です。

そのため、`chatgpt-music-app/` を作り、WordPressから独立したChatGPT App用シェルを用意しました。

### 5. ブラウザ単体で触れるWidgetを作成

ChatGPT Appへ接続する前でも操作感を確認できるよう、ブラウザ単体で動くWidgetを作りました。

初期機能は、

- KEY切り替え
- Major / Natural Minor
- コード発音
- コード進行の記録

です。

### 6. PCキーボード演奏に対応

マウスだけでなく、PCキーボードでも弾けるようにしました。

現在の基本配列は、

`A S D F G H J`

を左から右へ I〜VII に割り当てています。

ピアノの白鍵を横に弾く感覚に寄せつつ、今回は単音ではなくコード演奏なので、各キーでダイアトニックコードが鳴ります。

さらに、

`Shift + A〜J`

で7thコードを鳴らせるようにしています。

例: C Majorの場合

- A = C
- S = Dm
- D = Em
- F = F
- G = G
- H = Am
- J = Bdim
- Shift + A = Cmaj7
- Shift + G = G7

### 7. 固定URLでテストできる環境を作成

毎回HTMLをダウンロードして確認するのは非効率だったため、公開Preview専用リポジトリを作りました。

本体の `attripthema` はPrivateのまま維持し、公開しても問題ないテスト用コードだけをこのリポジトリへ分離しています。

GitHub Pagesを有効化し、以下の固定URLで確認できるようになりました。

https://attrip.github.io/-attrip-music-preview-/

これにより、今後は以下のループで開発できます。

1. GitHub上のコードを修正
2. 同じPreview URLへ反映
3. 実際に弾いて操作感を確認
4. 感想・不具合・改善案を共有
5. 再度GitHubを修正

## 現在できること

- KEY選択
- Major / Natural Minor切り替え
- ダイアトニックコード表示
- マウスでコード演奏
- A S D F G H J でコード演奏
- Shift + A〜J で7thコード演奏
- Web Audio APIによる簡易発音
- コード進行の履歴表示

## 今後の候補

まだ実装していないものです。

- 無料SoundFont / ピアノ音源
- Rhodes / Organ / Padなどの音色切り替え
- コード進行の自動再生
- BPM同期
- Beat Roomとの同期
- Bass / Melodyトラック
- inversion
- 9th / 11th / 13th
- MIDI OUT
- Logic Pro連携
- MIDIファイル書き出し
- ChatGPT Apps SDK / MCP連携
- AIによるコード進行生成

## 開発方針

重要なのは、最初から全部を作らないことです。

基本方針は、

> 触る → 鳴る → 感想を得る → 直す

です。

音楽理論の説明ツールではなく、実際に弾きながら考えられる道具として育てます。

## 関連リポジトリ

本体テーマ:

`attrip/attripthema`

公開Preview:

`attrip/-attrip-music-preview-`

---

Started: 2026-08-19
