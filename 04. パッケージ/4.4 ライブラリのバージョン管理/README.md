## go getでライブラリを取得
- `go get`コマンド
  - Goのライブラリなどを取得するコマンド
  - 依存するライブラリも一緒に取得
  - 指定した場所からダウンロード&インストール
  - 一度取得したものは再度取得しない
  - `-u`オプションでダウンロードを強制
```zsh
$ go get github.com/hoge/foobar
$ ls $GOPATH/src/github.com/hoge/foobar
README.md   foobar.go
```
