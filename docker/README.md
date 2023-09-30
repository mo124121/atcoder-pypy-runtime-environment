# docker imageについて

いずれもビルド済みイメージを公開しています。
https://hub.docker.com/r/mo124121/atcoder-pypy

## Dockerfile

ryeを使ってジャッジに入っているライブラリのほか、ツール等の導入が済んでいるイメージです。

## Dockerfile.original

下記ページにあるスプレッドシートに記載されたインストール方法に可能な限り合わせたイメージです。

https://atcoder.jp/contests/language-test-202301

ただし、そもそもジャッジのベース環境そのものは公開されてなさそうなので、あくまで雰囲気です。


## Dockerfile.original-slim

基本的には上記同様ですが、マルチステージビルドを用いてイメージサイズを削減しています。
あんまり動作検証はしていないです。