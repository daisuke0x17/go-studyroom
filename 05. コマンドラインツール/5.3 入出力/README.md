## 入出力の抽象化
- `io.Reader`と`io.Writer`
  - 入出力を抽象化したioパッケージで提供される型

## defer
- 関数の遅延実行
  - 関数終了時に実行
  - 引数の評価はdefer呼び出し時
  - スタック形式で実行（Last In First Out）

## forの中でdeferは避ける
- 予約した関数の呼び出しはreturn時に実行
  - forの中を関数に分割
```go
for _, fn := range fileNames {
	err := readFile(fn)
	if err != nil{/* エラー処理 */}
}

func readFile(fn string) error {
	f, err := os.Open(fn)
	if err != nil { return err }
	defer f.Close()
	// fを使った処理
}
```