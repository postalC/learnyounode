**非同期** ファイルシステムのメソッドを使ってファイルの改行数を出すアプリを書いてください。`cat file | wc -l`と同じようなアプリです。

アプリの一つ目のコマンドライン引数はそのファイルのパスです。

----------------------------------------------------------------------
# ヒント

解決方法は前のとほとんど一緒です。ただ今回は Nodeの良い方法を使わないといけないです：**非同期(ASYNC)** 。

`fs.readFileSync()` ではなく `fs.readFile()` を使わないといけません。返り値を受け取るのではなく、二つ目の引数としてコールバック関数を使って値を受け取ってください。コールバックについて勉強したい場合はこれを読んでください： https://github.com/maxogden/art-of-node#callbacks

通常、Nodeでは習慣的にコールバックには以下の様な引数を使うことに注意してください：

```js
function callback (err, data) { /* ... */ }
```

エラーであれば、`err` は `null` なので、一つ目の引数でエラーかどうか判別出来ます。エラーがなければ二つ目の引数には大切な`Buffer`オブジェクトが入っています。`readFileSync`と同じようにファイルパスとコールバック引数の間に`"utf8"`を入れてもいいです。その場合は`Buffer`のかわりに`String`が返ります。

`fs` モジュールのドキュメントはブラウザーでこのリンクを見てください:
  {rootdir:/node_apidoc/fs.html}

----------------------------------------------------------------------
