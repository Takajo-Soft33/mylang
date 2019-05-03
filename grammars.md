## コメント
```
# これはコメントです
#から行末までがコメントになります
(#
  複数行のコメントです
  (# ネストできます #)
#)
```

## 制御構文

### if-elif-else
```
if x % 3 == 0 and x % 5 == 0
  print! "FizzBuzz"
elif x % 3 == 0
  print! "Fizz"
elif x % 5 == 0
  print! "Buzz"
else
  print! x

if y < 0, y = 0 # 単一行
```

### case
```
case m
  0 -> n + 1
  _ -> A(m-1, A(m, n-1))
```

### do-while
```
var x = 1
do
  x += 1
  while x < 9
  print! x

do while n > 0
  n >>= 1
```

## 定数
```
val x = 1
val x: Int = 1
val x @defer: Int # 遅延代入 (定義時に代入しない場合、@defer注釈を付けないとエラーになります)
```

## 変数
```
var x = 1
var x: Int = 1
var x: Int
```

## 関数
```
c = 1     # 定数関数。定数と定数関数の違いは、正格評価か、遅延評価かです
f x = x   # 恒等関数
f(x: Int) = x # Int型のみ
f(x, y: Int): Int = x + y
f(x: Int, y: String) = (x as String) + y
k x y = x

# 複数行の定義
max(x, y) =
  if x < y
    return y
  return x

# 多重定義
fib 0 = 0
fib 1 = 1
fib[n > 1](n: Int) = fib(n - 1) + fib(n - 2)

# 副作用のある関数
_count = 0
count! = # 副作用のある関数で、名前の末尾が!でない場合は、@sideEffect注釈を付けないとエラーになります
  c = _count
  _count += 1
  return c
```

### ラムダ式
```
succ = x -> x + 1
add = (x, y) -> x + y
curriedAdd = x -> y -> x + y
addInt = (x, y: Int) -> x + y
```

## モジュール
他のモジュールに組み込んだりもできる
```
ModA = module
  ::staticConst1 = 1
  ::staticMethod1(x) = ...
  
  var _var1 = 1 # 名前の先頭が_のとき、自動的にprivateになる
  var _var2 @public = 1 # @public注釈によって強制public化
  var var3 =
  
  _con1 = 1 # private定数
  con2 = 2 # public定数
  con3 @protected = 3 # protected定数

ModA.staticConst1
```

## クラス
newできるモジュール
```
Counter = class
  var _count
  construct!(init: Int) = # コンストラクタconstruct!
    _count = init
  count! =
    c = _count
    _count += 1
    return c
```

## インポート
```
import "openssl"
import "./example1"
import "openssl" as OSSL
import {Cipher} from "openssl"
```

## エクスポート
```
import "std"
export main! _ = std.out.print! "hello\n"

export OpenSSL @default = module
  ::Cipher = module
    ...
```

## misc.

### staticスコープ
```
color = Color.BLUE
color: Color = BLUE

case color
  Color.BLUE ->
```