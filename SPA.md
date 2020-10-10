# GitHub Pages で SPA を実現する

プレーンな JavaScript を使って GitHub Pages で SPA を実装するための Tips たち。  
正直フレームワークを使った方がいいと思う。
低レイヤーに興味のない実用コードが欲しい方は回れ右。

* [rafgraph/spa-github-pages: Host single page apps with GitHub Pages](https://github.com/rafgraph/spa-github-pages)

## 要件

* ページは2種類
  * index
  * content （複数）
* ページの中身は JSON で定義
* 各ページのパーマリンクは欲しい
* 履歴もちゃんとしたい（ブラウザバック）

## 方法

* `history.pushState` で URL を書き換えられる（要件）
  * `#` でやる方法もあるけど本来の用途ではなく古いしダサい
* フレームワークだったらページ毎のファイルを用意して動的に読み込むんだろうけどめんどくさいので最初からindex.htmlに書いておいて非表示にする
  * ページが2種類しかない＆コンテンツは動的に生成するからできる
  * 通信によるオーバーヘッドがないので爆速
* `/<repository>` が URL に含まれるので対応する
* 完成。めでたしめでたし。でもちょっと待って欲しい。
* 普通にファイルを置くとindexを通さない外部サイトからトップページ以外に直接アクセスしたときに 404 で困る
* GitHub Paged では 404.html が置ける
  * スクリプトも書ける
    * `window.location.replace()`
      * 履歴に残さない
* index にリダイレクトさせて判定する
  * ここには `#` を使う
* 存在するページなら更にリダイレクトする
  * `history.replaceState`
    * 履歴に残さない
* 余談
  * 要件が複雑だともうちょっと工夫が要るかも
