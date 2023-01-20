## 条件分岐: if
- 指定した条件で分岐
  - `else`は条件にアタはまらない場合
  - `else`の後に`if`をさらに追加可能
  - `else`や`else if`は省略可能
- Goの特徴
```go
// ()がいらない
if x == 1 {
	println("xは1")
} else if x == 2 {
	println("xは2")
} else {
    println("xは1でも2でもない")	
}

// できない
if a == 0
{
}

// できない
if(a == 0) fmt.Println(a)

// 代入文を書く
if a := f(); a > 0 {
	fmt.Prinrln(a)
} else {
	fmt.Println(2*a) // aはifとelseのブロックで利用可能
}
```
※Goはコンパイル時に後ろに改行があると自動でセミコロンを代入

※改行の前が`{`などの文字だと差し込まない