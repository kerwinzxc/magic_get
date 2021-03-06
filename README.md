#POD Flat Reflection (Magic Get) [![Build Status](https://travis-ci.org/apolukhin/magic_get.svg?branch=master)](https://travis-ci.org/apolukhin/magic_get) [![Build Status](https://travis-ci.org/apolukhin/magic_get.svg?branch=develop)](https://travis-ci.org/apolukhin/magic_get)

This C++14 library is meant for accessing structure elements by index and providing other std::tuple like methods for user defined POD types.


[Latest documentation](http://apolukhin.github.com/magic_get/index.html)

[Pre Boost version](https://github.com/apolukhin/magic_get/tree/pre_boost)


### Motivating example
```c++
#include <iostream>
#include "boost/pfr.hpp"

struct my_struct { // no ostream operator defined!
    int i;
    char c;
    double d;
};

int main() {
    using namespace boost::pfr::flat_ops; // for ostream operator out-of-the-box for all PODs!

    my_struct s{100, 'H', 3.141593};
    std::cout << "my_struct has " << boost::pfr::flat_tuple_size<my_struct>::value
        << " fields: " << s << "\n";
}


```

Outputs:
```
my_struct has 3 fields: {100, H, 3.14159}
```


### Requirements and Limitations

* C++14 compatible compiler (GCC-5.0+, Clang, ...)
* Static variables are ignored

C++14 limitations (C++17 fixes those):
* T must be POD and must not contain references nor bitfields
* T must not contain pointers to user defined types
* Enums will be returned as their underlying type

### License

Distributed under the [Boost Software License, Version 1.0](http://boost.org/LICENSE_1_0.txt).
