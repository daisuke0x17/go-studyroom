## 条件分岐：if
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

## 条件分岐：switch
- `break`は不要
  - 何も記述しないと`break`になる
- `case`をまたぎたいときは`fallthrough`
```go
switch a {
case 1, 2:
	fmt.Println("a is 1 or 2")
default:
	fmt.Println("default")
}
```
- `case`に式が利用可能
  - 大量の`if-else`をつなぐより見通しGood
```go
switch{
case a == 1:
	fmt.Println("a is 1")
}
```

## 繰り返し：for
- 繰り返しは`for`のみ
````go
// 初期値;継続条件;更新文;
for i := 0; i <= 100; i = i + 1 {
}

// 継続条件のみ
for i <= 100 {
}

// 無限ループ
for {
}

// rangeを利用した繰り返し
for i, v := range []int{1, 2, 3}{
}
````
- `break`によるループからの抜け出し
  - Goには`goto`も存在
```go
// breakによる無限ループの脱出
for {
	if i%2 == 1 {
		break
    }
}

// ラベル指定のbreak
func main(){
	var i int
LOOP:
	for {
		switch {
		case i%2 == 1:
			break LOOP
        }
		i++
    }   
}
```