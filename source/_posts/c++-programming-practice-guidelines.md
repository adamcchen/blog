---
title: C++编程实践
date: 2019-12-07 12:00:00
tags: C++
---

# 阅读本文你将收获什么？
知道更加简单、高效、可维护的C++代码是什么样的。

# 好的编程实践
- 断行必须很明显
```c++
// YES
```
```c++
// NO
```

- 断行必须很明显
```c++
// YES
std::cout << std::hex <<
             intValue << endl;
```
```c++
// NO
std::cout << std::hex <<
intValue << endl;
```

- 使用`using std::cout`或者`std::cout`替代`using namespace std`
```c++
// YES
using std::cout;
using std::endl;

cout << "hello world" << endl;
``
// YES
std::cout << "hello world" << std::endl;
``
```c++
// NO
using namespace std;

cout << "hello world" << endl;
``

- 使用`const`替代`#define`
```c++
// YES
const double PI = 3.1415; 
```
```c++
// NO 
#define PI 3.1415
```

- 使用`iostream`替代`stdio.h`
```c++
// YES
#include <iostream>
```
```c++
// NO 
#include <stdio.h>
```

- 使用C++风格的类型转换
```c++
// YES
double doubleValue = static_cast<double>(intValue);
```
```c++
// NO
double doubleValue = (double)intValue;
```

- 使用nullptr替换NULL
```c++
// YES, https://www.cnblogs.com/porter/p/3611718.html
ptr = nullptr;
```
```c++
// NO
ptr = NULL;
```

- 尽量多地使用const

# 参看
[1] [Google开源项目风格指南英文版](https://github.com/google/styleguide)

[2] [Google开源项目风格指南中文版](https://github.com/zh-google-styleguide/zh-google-styleguide)

[3] [geosoft.no的编码风格指南英文版](https://geosoft.no/development/cppstyle.html)

[4] [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)
