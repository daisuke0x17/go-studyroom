## プログラム引数
- プログラム実行時に渡される引数
  - プログラムに対して外から渡されるデータ・情報
  - ターミナル上でコマンドを入力する際にみるやつ
  - コマンドライン引数 = プログラム引数
```zsh
$ echo hello // hello がコマンドライン引数
> hello
```

## プログラム引数の取得
- `os.Args`を利用 
  - プログラム引数が入った文字列型のスライス 
  - 要素のひとつめ（0番目）はプログラム名
```go
func main(){
	fmt.Println(os.Args)
}
```
```zsh
$ ./main hello world
> [./main hello world]
```