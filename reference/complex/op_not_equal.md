#operator!=
* complex[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class T>
  bool operator!=(const complex<T>& lhs,
                  const complex<T>& rhs);           // C++03

  template <class T>
  constexpr bool operator!=(const complex<T>& lhs,
                            const complex<T>& rhs); // C++14

  template <class T>
  bool operator!=(const complex<T>& lhs,
                  const T& rhs);                    // C++03

  template <class T>
  constexpr bool operator!=(const complex<T>& lhs,
                            const T& rhs);          // C++14

  template <class T>
  bool operator==(const T& lhs,
                  const complex<T>& rhs);           // C++03

  template <class T>
  constexpr bool operator==(const T& lhs,
                            const complex<T>& rhs); // C++14
}
```

##概要
非等値比較を行う。


##戻り値
`lhs.`[`real`](complex/real.md)`() != rhs.`[`real`](complex/real.md)`() || lhs.`[`imag`](complex/imag.md)`() != rhs.`[`imag`](complex/imag.md)`()`


##備考
引数の型が `const T&` の場合、虚部（[`imag`](imag.md)`()`）は `T()`、あるいは、`0.0` とみなされる。


##例
```cpp
#include <iostream>
#include <complex>

int main()
{
  std::complex<double> c1(1.0, 2.0);
  std::complex<double> c2(1.0, 4.0);
  std::cout << std::boolalpha;
  std::cout << c1 << " != " << c1 << ":" << (c1 != c1) << std::endl;
  std::cout << c1 << " != " << c2 << ":" << (c1 != c2) << std::endl;
  std::cout << c1 << " != " << 1.0 << ":" << (c1 != 1.0) << std::endl;
  std::cout << 4.0 << " != " << c2 << ":" << (4.0 != c2) << std::endl;
}
```
* !=[color ff0000]

###出力
```
(1,2) != (1,2):false
(1,2) != (1,4):true
(1,2) != 1:true
4 != (1,4):true
```


##参照
- [N3302 Constexpr Library Additions: complex, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)


##関連項目

| 名前                        | 説明                                           |
|-----------------------------|------------------------------------------------|
| [`operator==`](op_equal.md) | 等値比較を行う。                               |
| [`real`](complex/real.md)   | 実部を取得、あるいは、設定する。（メンバ関数） |
| [`imag`](complex/imag.md)   | 虚部を取得、あるいは、設定する。（メンバ関数） |
