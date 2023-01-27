## インタフェースと抽象化
- 抽象化
  - 具体的な実装を隠して振る舞いによって共通化
  - 複数の実装を同質のものとして扱う
- インタフェースによる抽象化
  - Goの抽象化は`interface`のみ！

## インタフェース
- インタフェースはメソッドの集まり
- 型TがインタフェースIを実装しているとは
  - インタフェースで定義されているメソッドを全て持つ
  - 型TはインタフェースI型として振る舞うことが可能
- 必要なところ（引数や戻り値）だけ見せて具体的な処理は隠蔽

## interface{}
- empty interface
- メソッドリストが空のインタフェース
  - つまりどの型の値も実装していることになる
  - JavaのObject型のような使い方が可能
 
## 関数にインターフェースを実装
- 関数にメソッドを持たせる
  - 頻繁には使わないが、全く使わないわけでもない
```go
type Func func() string

func(f Func) String() string{return f()}

func main(){
	var s fmt.Stringer = Func(func() string{
		return "hi"
    })
	fmt.Println(s)
}
```
- net/httpに良い例が存在
```go
// 関数の型を定義
type HandlerFunc func(ResponseWriter, *Request)
// 上で定義した型（関数）にメソッドを持たせる
func (f HandlerFunc) ServeHTTP(w ResponseWriter, r *Request)

// HandlerFuncはServeHTTPメソッドを持っているのでHandlerを実装したことになる！
type Handler interface{
    ServeHTTP(ResponseWriter, *Request)
}
```

## スライスとインタフェース
- 実装していてもスライスは互換性がない
  - コピーは`for`を回すしかない
```go
ns := []int{1, 2, 3, 4}

//できない
var vs []interface{} = ns
```

## インタフェースの実装チェック
- コンパイル時に実装しているかチェック
  - インタフェース型に代入
  - 慣例的な書き方なのでOSSで見かけるかも
```go
type Func func() string
func(f Func) String() string {return f()}

// これでインタフェースを実装しているかコンパイル時にチェック
var _ fmt.Stringer = Func(nil)
```

## 型アサーション
- インタフェース.(型)
  - インタフェース型の値を任意の型にキャスト
  - 第2戻り値にキャストできるかどうかが返る
```go
var v interface{}

v = 100
n, ok := v.(int)
fmt.Println(n, ok)
```

## 型スイッチ
- 型によって処理をスイッチ
```go
var i interface{}
i = 100
switch v := i.(type){
    case int:
		fmt.Println(v * 2)
    case string:
		fmt.Println(V + "hoge")
    default:
		fmt.Println("default")
}
```

## インタフェースの設計
- メソッドリストは小さく
  - 共通点を抜き出して抽象化はしない
  - 一塊の振る舞いを一つのインタフェースにする
  - 型を使うユーザが触れる部分がインタフェースでなくてもよい
    - 内部にエンジンやドライバの形で抽象化したものを持つ感じ
    - `http.Client`内部の`http.RoundTripper`のようなイメージ
- 型階層は作れない
  - Goでは型階層は作れない
  - 抽象化はすべてインタフェース
  - 型階層ではなくコンポジットで表現