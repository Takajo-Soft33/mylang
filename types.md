# 型システム
Calculus of Inductive Construction + クラスベースオブジェクト指向

* ポリモーフィズム（ジェネリック型）
* 依存型（行列型など）
* 型コンストラクタ

## 型
### Union
直和型
```
val UniAB = A | B
val x: UniAB = A()
val a: A = x as A
```

### Tuple
直積型、要素に名前がつけられる
```
val t1 = (a, b)
val t2 = (x = 10, y = 20)
```

