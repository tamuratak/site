#arg
```cpp
namespace std {
  template <class T>
  T arg(const complex<T>& x);

  FloatingPointType arg(ArithmeticType x);	// 追加のオーバーロード：C++11 から
}
```

##概要
複素数値の偏角を得る。arg は argument（偏角）の略。

なお、C++11 で追加されたオーバーロードは、以下のように規定されている。

- 実引数の型が `long double` の場合、`complex<long double>` にキャストされているかのように振る舞う。
- そうでなくて、実引数の型が `double` か整数型の場合、`complex<double>` にキャストされているかのように振る舞う。
- そうでなくて、実引数の型が `float` の場合、`complex<float>` にキャストされているかのように振る舞う。

また、これらの追加のオーバーロードが関数テンプレートなのか否か、あるいは、引数が参照型なのか否かなどについては、規格では何も言及されていない。


##戻り値
引数 `x` の偏角。単位はラジアン。[`atan2`](/reference/cmath/atan2.md)`(`[`imag`](imag.md)`(x), `[`real`](real.md)`(x))`。


##備考
- 規格には、上記の戻り値に記載されている以上の規定・説明は無い。  
なお、C99 の規格にある本関数と同等の関数群（`complex.h` ヘッダの `carg`、`cargf`、`cargl`の 3 つ。それぞれ C++ の `arg<double>`、`arg<float>`、`arg<long double>` に相当）では、
本関数は実軸の負の領域すべてを分岐截断とすること、および、戻り値は `[-π, π]` の区間であることが記載されている。
- [`atan2`](/reference/cmath/atan2.md) は、処理系が ISO IEC 60559（IEEE 754 と同一）に準拠していない場合、両方の引数が `0` の場合には定義域エラー（domain error）としても良いとされているので注意（つまり、`0` の偏角を求めようとするとエラーとなる）。
ISO IEC 60559 に準拠している場合、両方の引数が `0` の場合には戻り値が `0` であることが規定されている。
- 処理系が ISO IEC 60559 に準拠しているかどうかは、C99 の場合はマクロ `__STDC_IEC_559_COMPLEX__` が `1` に定義されている事で判別可能であるが、
C++ の規格書には該当する記載を見つける事ができなかった。


##例
```cpp
#include <iostream>
#include <complex>

int main()
{
  std::complex<double> c(1.0, 2.0);
  std::cout << "arg( " << c << " ) = " << std::arg(c) << std::endl;
}
```
* arg[color ff0000]
* iostream[link /reference/iostream.md]
* complex[link /reference/complex.md]

###出力
```
arg( (1,2) ) = 1.10715
```


##参照
|                                    |                                        |
|------------------------------------|----------------------------------------|
| [`real`](real.md)                  | 複素数の実部を得る。                   |
| [`imag`](imag.md)                  | 複素数の虚部を得る。                   |
| [`abs`](abs.md)                    | 複素数の絶対値を得る。                 |
| [`norm`](norm.md)                  | 複素数体のノルムを得る。               |
| [`conj`](conj.md)                  | 共役複素数を得る。                     |
| [`proj`](proj.md)                  | リーマン球面への射影を得る。           |
| [`polar`](polar.md)                | 指定した絶対値と偏角の複素数値を得る。 |