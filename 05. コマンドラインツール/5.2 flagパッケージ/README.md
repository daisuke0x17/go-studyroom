## flagパッケージ
- フラグ（オプション）を便利に扱うパッケージ
```go
// 設定される変数のポインタを取得
var msg = flag.String("msg", "デフォルト値", "説明")
var n int
func init(){
	// ポインタを指定して設定を予約
	flag.IntVar(&n, "n", 1, "回数")
}

func main(){
	// ここで実際に設定される
	flag.Parse()
	fmt.Println(string.Repeat(*msg, n))
}
```

```zsh
$ ./main -msg=こんにちは -n=2
> こんにちはこんにちは
```
## flagパッケージとプログラム引数
- `flag.Args`関数を利用
  - `os.Args`ではフラグ自体も含まれる
  - `flag.Args`関数はフラグ分は除外される
  - `flag.Args`ではプログラム名は含まれない
```zsh
func main(){
  fmt.Println(flag.Args())
}
```
```zsh
$ ./main -msg=こんにちは -n=2 やぁ
> やぁ
```