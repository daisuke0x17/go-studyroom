# Goに触れる<!-- omit in toc -->
## 目次<!-- omit in toc -->
- [1.1 Goとは？](#11-goとは)
  - [Goとは？](#goとは)
  - [Goが開発された理由](#goが開発された理由)
  - [Go1の後方互換](#go1の後方互換)
  - [Go開発のプロセスとGo2](#go開発のプロセスとgo2)
  - [Goの特徴](#goの特徴)
- [1.2 Goが利用できる領域](#12-goが利用できる領域)
  - [Goの利用状況](#goの利用状況)
  - [gRPCとGo](#grpcとgo)
  - [Google App Engine for Go](#google-app-engine-for-go)
  - [Goで開発されているOSS](#goで開発されているoss)
  - [コマンドラインツールでの利用](#コマンドラインツールでの利用)
  - [Goで書かれたCLIツール](#goで書かれたcliツール)
  - [組み込みやIoTでの利用](#組み込みやiotでの利用)
  - [Tiny Go](#tiny-go)
  - [GopherJSでフロントエンド開発](#gopherjsでフロントエンド開発)
  - [Go Mobileでモバイルアプリ開発](#go-mobileでモバイルアプリ開発)
- [1.3 Goを学ぶには](#13-goを学ぶには)
  - [Goを学ぶ理由](#goを学ぶ理由)
  - [公式チュートリアルで学ぶ](#公式チュートリアルで学ぶ)
  - [go.dev](#godev)
  - [書籍で学ぶ](#書籍で学ぶ)
  - [公式ドキュメントを読んで学ぶ（重要）](#公式ドキュメントを読んで学ぶ重要)
  - [Goをコミュニティで学ぶ](#goをコミュニティで学ぶ)
  - [Woman Who Go](#woman-who-go)
  - [Student Go](#student-go)
  - [海外カンファレンスで学ぶ](#海外カンファレンスで学ぶ)
- [1.4 Hello World](#14-hello-world)
  - [Go Playground](#go-playground)
  - [Goのコメント](#goのコメント)
  - [プログラムが実行されるまでの流れ](#プログラムが実行されるまでの流れ)
  - [プログラムに問題がある場合](#プログラムに問題がある場合)
  - [プログラムはどこから実行されるのか](#プログラムはどこから実行されるのか)
- [1.5 Goのインストールと設定](#15-goのインストールと設定)
  - [開発に必要なもの](#開発に必要なもの)
  - [Goの開発環境のインストール](#goの開発環境のインストール)
  - [コンパイルと実行](#コンパイルと実行)
  - [GoLand](#goland)
  - [aaa](#aaa)
- [1.6 Goの開発ツール](#16-goの開発ツール)
  - [コードの書式を揃える](#コードの書式を揃える)
  - [コードの品質を保つ](#コードの品質を保つ)
  - [PRレビューで静的解析ツールを使用](#prレビューで静的解析ツールを使用)
  - [デバッグ](#デバッグ)

## 1.1 Goとは？
### Goとは？
- Googleが開発したプログラミング言語
  - 2009年11月に最初のバーションをOSSで公開
- 特徴
  - シンプルな言語設計と文法
  - 並行プログラミング
  - 豊富な標準ライブラリ
  - シングルバイナリ・クロスコンパイル
### Goが開発された理由
- Google内の課題を解決するために開発
  - 開発速度の低下
  - マルチコア時代のシステム言語
  - 軽量プログラミング言語の盛り上がり
  - 静的解析がしやすい
### Go1の後方互換
- Go1の間は言語の後方互換が保たれる
  - `Go1.x`の間は互換性が有効
### Go開発のプロセスとGo2
- 開発プロセス
  - 実際にGoを使った中で問題を発見
  - 解決策をコミュニティに提案し議論
  - 実装して評価
  - 問題なければリリース
- Go2とは？
  - 明確なターゲットはない
  - `Go1.x`の互換性が保てなくなるような変更が必要になればGo2の登場
  - 現状，Go2は概念
### Goの特徴
- スクリプト言語の書きやすさ
- 型のある言語の厳密さ
- 機能を増やすことで言語を拡張していくことはしない
- 並行プログラミング
  - ゴールーチン
    - 軽量なスレッドに近いもの
  - チャネル
    - ゴールーチン間で安全にデータをやりとりできる
- 豊富な標準ライブラリ
  - https://golang.org/pkg/
- 周辺ツールの充実
  - go toolとして標準/準標準で提供
  - IDEによらない独立したツールとして提供
  - `go build` `go test` `go doc` `gofmt` `go vet` `gopls` など
- シングルバイナリ・クロスコンパイル
  - 開発環境とは違うOSやアーキテクチャ向けのバイナリが作れる
  - 環境変数の`GOOS`と`GOARCH`を指定する`
```
Goに入ってはGoに従え = 言語の思想を理解することが大切
```
## 1.2 Goが利用できる領域
### Goの利用状況
- https://blog.golang.org/survey2018-results
- web開発，DevOpsでの利用が多い
- GUI，AI，ゲームでの利用は少ない
### gRPCとGo
- Googleが開発したRPCのプロトコル
### Google App Engine for Go
- Googleが提供するPaaS
- Goのインスタンスの起動が恐ろしく早い
### Goで開発されているOSS
- Docker
- Kubernetes
- gVisor
### コマンドラインツールでの利用
- 環境に依存しない
  - シングルバイナリになるので依存するものがない
  - クロスコンパイルができるので他のOS向けにコンパイル可能
- 標準パッケージが豊富
  - コマンドラインツールを作るために必要な機能が標準で存在
### Goで書かれたCLIツール
- peco
- ghq
- Hugo
### 組み込みやIoTでの利用
- 組み込み向けの開発が楽
  - クロスコンパイルが可能
  - ランタイムがあるのでバイナリサイズが大きくなる問題がある
- GOBOTの利用
  - さまざまなデバイス向けのライブラリを集めたもの
    - ドローン，Rasberry Piなど
### Tiny Go
- 組み込み向けのGoのサブセット
  - バイナリが小さい
### GopherJSでフロントエンド開発
- サードパーティプロジェクト
- GoからJSを生成するツール群
  - ゴールーチンとチャネルに対応
  - ほとんどの標準パッケージに対応
### Go Mobileでモバイルアプリ開発
- Goでモバイルアプリを作るツール群
- 2通りのスタイル
  - Goだけで動く
  - Goで書いたライブラリを呼び出す
- Ebiten（Go製の2Dゲームライブラリ）

## 1.3 Goを学ぶには
### Goを学ぶ理由
- 多くのプロダクトで採用
- チーム開発に向いている
  - 静的型付け
    - レビューコストが低い
    - コンパイルでエラーを見つけられる
  - 文法がシンプル
- パフォーマンスが良い
  - ゴールーチンとチャネル
  - バイナリになる
### 公式チュートリアルで学ぶ
- A Tour of Go
  - https://tour.golang.org
### go.dev
- Goの学習教材や事例が紹介されているサイト
  - https://go.dev
  - Goチームが運営している（信頼性高）
### 書籍で学ぶ
- プログラミング言語Go
- みんなのGo言語
- Goならわかるシステムプログラミング
- Go言語による並行処理
### 公式ドキュメントを読んで学ぶ（重要）
- 言語仕様
- Go Code Review Comments
- Effective Go
- パッケージドキュメント
- 公式ブログ

※できるだけ本家を参考にすること（Qiitaなどの情報は古くなっている可能性あり）

※golang.jpは情報が古いので注意
### Goをコミュニティで学ぶ
- Goビギナーズ
- golang.tokyo
- Go Conference
- Gophers Slack
### Woman Who Go
- 女性とジェンダーマイノリティのGoコミュニティ
### Student Go
- 学生のGoコミュニティ
### 海外カンファレンスで学ぶ
- GopherCon

## 1.4 Hello World
### Go Playground
- サードパティパッケージも使える
- 複数ファイルも使える
- うまくいかない例
  - コメント中に`--`で始まる行を含む場合
- Chrome拡張機能
- コマンドラインから操作
### Goのコメント
- 行コメント
  - `//`から行末まで
- ブロックコメント
  - `/*`から`*/`まで
### プログラムが実行されるまでの流れ
1. コーディング（Goのコード）
2. コンパイル（機械語）
3. 実行
### プログラムに問題がある場合
- コンパイルエラーになる
  - エラーは英語だがしっかり読むことが大切
### プログラムはどこから実行されるのか
- main関数
  - プログラムの始まり＝エントリポイント
  - mainパッケージに存在
  - Goプログラムは初期化後，必ずここから実行
    - 厳密にはパッケージ変数やinit関数が先
  - プログラムを読む際は最初にmain関数を読む
  - Webサーバの場合はずっと実行
    - 代わりにHTTPハンドラを読む
  - 関数＝処理を意味のある形でまとめたもの

## 1.5 Goのインストールと設定
### 開発に必要なもの
- Goのツールチェイン（開発環境）
  - Goのソースコードを機械語に翻訳するためのコンパイラなど
- エディタ・IDE
- Git
  - `go tool`の中で使われている
### Goの開発環境のインストール
- 公式サイトからダウンロード
### コンパイルと実行
- `go build`
  - コンパイルして実行可能ファイル（バイナリ）を生成
- `go run`
  - コンパイルから実行まで行う
### GoLand
- JetBrains製のGoのIDE
  - 多くのGopherが使っている
  - 補完が高速
  - インターフェース実装へのジャンプ
  - リファクタリング機能
  - デバッガ
  - 有料
    - 学生は無料
### aaa
- wip

## 1.6 Goの開発ツール
### コードの書式を揃える
- gofmt
  - 読み方：ごーふむと
  - 標準のフォーマッタ
  - 絶対に使う
  - `-s` オプションで冗長な書き方をシンプルにできる
- goimports
  - import文を追加/削除
  - 未使用パッケージのimportはエラーなので必須
  - フォーマットもかける
  - `-s` オプションはない
### コードの品質を保つ
- go vet
  - バグといえるレベルの誤りを検出
  - コンパイラでは発見できないバグを見つける
    - go testを走らせれば自動で実行される（Go1.10から）
- golint
  - Goらしくないコードを検出
- errcheck
  - エラー処理のミスを検出
- statickcheck
  - サードパーティ製の静的解析ツールのセット
- GolangCI-Lint
  - サードパーティ製のLinter Runner
### PRレビューで静的解析ツールを使用
- reviewdog
  - レビュー時に自動で静的解析ツールを実行する
  - 機械的にチェックできることは機械に任せる
### デバッグ
- Delve
  - Go専用のデバッガでよく使われる
