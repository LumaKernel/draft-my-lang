言語を作る。

とりあえずパーサとランナーを作る。

# Motivation

理論的に使いやすい、そこそこ記述力のある言語を作る。
Golang のような書き味を目指す。

メモリモデルは特殊で、可算無限のメモリが使えることを仮定してありえん配置をする。ものすごいコピーする。
つまり全く実用的ではない。

# Goals

- Brainfuck Compatible

# Not Goals

- Package system
- JSON like object support

# ビルトイン型

- `bool`
- `byte`
- `bigint`
- `modint(bigint n)`
- `array(type t)`
- `pointer(type t)`
- `optional(type t)`

とりあえずここまで。以下も…いやいくつかはいいけどいくつかはやりたくない

- `func`
- `map(type t, type t)`
- `unit` ( and tuples ? )
- `ieee754_32`
- `ieee754_64`
- `float32 = ieee754_32`
- `float64 = ieee754_64`
- `complex(type float) = struct{real float; imag float; ...}`
- `struct`

# Literals

## Value

- `()` - `unit`
- `"abc"` - `array(byte)`
- `'a'` - `byte`
- `true`, `false` - `bool`
- `1` - `bigint`
- `x[4]`
- `x[-1]`
- `x[4:10]`
- `3 mod 10` - `modint(10)(3)`
- `@self` - `[][]byte`

## Type

- `[]t` - `array(t)`

Literals are *typed*.

# Operators

Ordered from weak to strong in each group.
Groups are independent each other.

## arithmetic

- `a + b`
- `a * b`,`a % b`
- `a ** b` (RTL)

## binary

- `a | b`
- `a & b`
- `a ^ b`
- `~a`

## boolean

- `a || b`
- `a && b`
- `a ^^ b`
- `!a`

## comparason: all are independent group

- `a == b`, `a != b`
- `a < b`, `a <= b`, `a > b`, `a >= b`

Notes:
- Not chainable
- No Comma Operator
- Different group MUST be parenthesesized before applying

# Examples

```
func main(input []byte) bigint {
  while {

  }
  while true {

  }
  sum := 0
  for i; 0; 10; 3 {
    if i < 3 {
      sum += 10
    }
  }
  return sum
}
```

