---
title: C++编程实践
date: 2019年12月7日
tags: C++
---

# 阅读本文你将收获什么？
知道更加简单、高效、可维护的C++代码是什么样的。

# 好的编程实践
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

- 使用0替换NULL
```c++
// YES
ptr = 0;
```
```c++
// NO
ptr = NULL;
```

- 尽量多地使用const


```c++
// YES

// NO
```
```c++
// YES

// NO
```
```c++
// YES

// NO
```
```c++
// YES

// NO
```

# 参看
[1] [Google开源项目风格指南英文版](https://github.com/google/styleguide)

[2] [Google开源项目风格指南中文版](https://github.com/zh-google-styleguide/zh-google-styleguide)

[3] [geosoft.no的编码风格指南英文版](https://geosoft.no/development/cppstyle.html)

[4] [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)
