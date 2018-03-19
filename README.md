# pyniconico

ニコニコ動画をpythonから扱うツールです。

サーバーに負荷をかけない範囲でお使いください。

## 使い方

python >= 3.5

Chrome(default) | Firefox | PhantomJS のいずれかがインストールされていること。

```bash
$ git clone https://github.com/Sakaki/pyniconico.git
$ cd pyniconico
$ pip install -r requirements.txt
$ python niconico.py -u username -p password download sm32831006
sm32831006
ゆるキャン△にハマるマン しめさば
Downloading: 100%|#######################################################################|Time: 0:00:24
Saved as .\ゆるキャン△にハマるマン.mp4
```

### マイリスト一覧

```bash
$ python niconico.py -u username -p password mylist
マジミラ2017 59835789
けものフレンズ 58720332
みんなの愛したゆゆ式 58076939
...
```

### マイリスト動画一覧

```bash
$ python niconico.py -u username -p password mylist_items マジミラ2017
マジミラ2017:
  sm1587618
  sm26470008
  sm28974414
  sm31401854
...
```

### マイリストからダウンロード

```bash
$ python niconico.py -u username -p password download --mylist ボカロ
ボカロ
【波音リツキレ音源】心做し 【UTAUカバー】 cillia
Downloading: 100%|#######################################################################|Time: 0:00:03
Saved as ./【波音リツキレ音源】心做し_【UTAUカバー】.mp4
【初音ミク】 声 【オリジナルPV】 はりー
Downloading: 100%|#######################################################################|Time: 0:00:16
Saved as ./【初音ミク】_声_【オリジナルPV】.mp4
【初音ミク】 Initial Song 【オリジナルMV】 40mP
Downloading: 100%|#######################################################################|Time: 0:00:14
Saved as ./【初音ミク】_Initial_Song_【オリジナルMV】.mp4
...
```

### mp3に変換

ffmpegをインストールし、実行可能となっている（PATHに登録されている）必要があります。

```bash
$ python niconico.py -u username -p password download --mp3 sm31606995
sm31606995
ハチ MV「砂の惑星 feat.初音ミク」 ハチ
Downloading: 100%|#######################################################################|Time: 0:00:22
Saved as .\ハチ_MV「砂の惑星_feat.初音ミク」.mp4
.\ハチ_MV「砂の惑星_feat.初音ミク」.mp3
...
```

## ブラウザ

'-d'オプションで使用するヘッドレスブラウザを変更できます。

### Chrome（デフォルト）

```bash
$ python niconico.py -u username -p password (-d chrome) mylist
```

### Firefox

geckodriver経由でアクセスを行います。64bit専用。

```bash
$ python niconico.py -u username -p password -d firefox mylist
```

### PhantomJS（非推奨）

PhantomJSを使用することは非推奨となっています。

niconico.pyと同じディレクトリにて、'npm install phantomjs'を実行してください。

```bash
$ npm install phantomjs
$ python niconico.py -u username -p password -d phantomjs mylist
```

## 動作環境

OS: Linux, MacOS, Windows (Windowsではnetrcが動きません)

Firefoxは64ビットのみサポート（geckodriverを入れ替えれば任意のアーキテクチャで動くと思います）

## netrc

ホームディレクトリに以下のような.netrcファイル(~/.netrc)を用意することで、ユーザー名及びパスワード入力を省略することができます。

```
machine   nicovideo
login     someone@mail.com
password  testpasswd
```

## GUI (gui.py)

ニコニコ動画のログインシステムが刷新され、gui.pyのメンテナンスが追い付いていません。

恐らく動かないと思いますので、改善されるまでしばらくお待ちください・・・

---

```bash
$ pip install requirements_gui.txt
$ python gui.py
```

で起動します。初回はユーザー名、パスワード、URLまたは動画IDをすべて入力する必要があります。

![nicovideo_dl](https://user-images.githubusercontent.com/980141/29494124-72a2b4d4-85de-11e7-894d-9112dbac6e03.png)

2回目以降はクッキーを用いてログインを試み、成功した場合はユーザー名やパスワードの入力なしでもダウンロードができます。

### まとめてダウンロード

マイリスト一括ダウンロードの「選択」ボタンを押してください。

![nicovideo_dl_mylist](https://user-images.githubusercontent.com/980141/29494138-a967c586-85de-11e7-91f5-d125775ae09e.png)

### mp3変換

設定ボタンからmp3変換を有効にし、ビットレートを調整してください。

![nicovideo_dl_settings](https://user-images.githubusercontent.com/980141/29494148-d805f75a-85de-11e7-8cfd-02e5635f4025.png)

## ライセンス

pyniconicoのソースコードのライセンスについては、LICENSEファイルを参照してください。

また、pyniconicoはWebDriverとしてFirefoxを利用可能とするため、geckodriverを実行可能ファイルとして同梱しています。

geckodriverのラインセンスは[こちら](https://www.mozilla.org/en-US/MPL/2.0/)を参照してください。
