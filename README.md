# atcoder-pypy-runtime-environment

AtCoderにPyPyで参加するための欲張りセット

## 検証された環境

### devcontainer

- Ubuntu 22.04 (WSL2)
- docker
- Visual Studio Code
- Remote development拡張機能

本リポジトリをクローン後、当該ディレクトリをVSCodeで開いた後、"open folder in container"等で開けば一発で環境が整います。

### rye

- Ubuntu 22.04 (WSL2)
- [rye](https://rye-up.com/guide/installation/)

ryeはPyPyの導入から仮想環境の作成、pipパッケージのインストールまで一式やってくれるツールです。

同様にディレクトリを手配したうえで、
下記コマンドを打てば仮想環境が構築されます。

```
$ rye sync
```

ただし、pipパッケージのビルドが発生する都合、依存する外部ライブラリの事前導入が必要です。  
必要に応じてDockerfileを参考に導入してください。

Windowsでの動作は未検証です。

ぶっちゃけ手元でPyPyを動かす必要性はそんなにないので（え？）、もし動かない場合、CPythonを使うようにしてしまえばたぶん動きます。

```
$ rye pin 3.11.4
$ rye sync
```

## インストールされているツール

- online-judge-tools
- atcoder-tools
- atcoder-cli ※node.jsのパッケージなので、ryeだけだと入りません。

 devcontainerで開いた場合、setting/.atcodertools.tomlをatcoder-toolsが見るパスにバインドマウントしているので、設定をする場合はこちらを編集すればよいです。

## docker imageについて

[こちらを参照](docker/README.md)

## その他メモ

### pip install / rye syncをするとき時間がかかる

ビルド済みパッケージが公開されているCPythonと異なり、PyPyの場合は各種ライブラリのビルドが走る関係で時間がかかります。仕様です。
