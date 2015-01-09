#cbegin (C++11)
```cpp
const_iterator cbegin() const;
```

##概要
`*this` 内の全てのサブマッチを列挙するため、先頭のサブマッチを指すイテレータを返す。


##戻り値
先頭のサブマッチを指すイテレータ


##備考
- 「先頭のサブマッチ」は、正規表現にマッチした文字列全体を指す。
- 本メンバ関数で返されるイテレータは、[`begin`](begin.md) で返されるイテレータと型も含め完全に同一である。


##例
```cpp
#include <iostream>
#include <regex>

int main()
{
  const char s[] = " abc 0123 defgh ";
  const std::regex re("(\\w+) (\\d+) (\\w+)");

  std::cmatch m;
  if (std::regex_search(s, m, re)) {
    for (auto it = m.cbegin(), end = m.cend(); it != end; ++it) {
      std::cout << "str() = '" << it->str() << "', "
        "range = [" << it->first - s << ", " << it->second - s << "), "
        "matched = " << std::boolalpha << it->matched << std::endl;
    }
  } else {
    std::cout << "not match" << std::endl;
  }
}
```
* iostream[link ../../iostream.md]
* regex[link ../../regex.md]
* cmatch[link ../match_results.md]
* regex_search[link ../regex_search.md]
* cbegin[color ff0000]
* cend[link cend.md]
* str[link str.md]

###出力
```
str() = 'abc 0123 defgh', range = [1, 15), matched = true
str() = 'abc', range = [1, 4), matched = true
str() = '0123', range = [5, 9), matched = true
str() = 'defgh', range = [10, 15), matched = true
```


##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): -
- [Clang, C++11 mode](/implementation.md#clang): 3.0, 3.1, 3.2, 3.3, 3.4, 3.5, 3.6
- [GCC](/implementation.md#gcc): -
- [GCC, C++11 mode](/implementation.md#gcc): 4.9.0, 4.9.1, 5.0.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??

###備考
GCC(libstdc++) のバージョン 4.9.2 までは、`cbegin` が誤ったイテレータを返す。これは 4.9.3 以降で修正される予定である。