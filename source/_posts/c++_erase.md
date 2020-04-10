---
title: c++ erase的注意事项
date: 2019-07-12 21:23:43
tags:
  - c++
  - string
---

先看一段正常的代码

```
#include <iostream>
#include <string>
using namespace std;

int main() {

    string str = "123456789";
    str.erase(str.begin() + 2, str.end() - 2);
    cout << str;

    return 0;

}
```

移除中间的一段字符  
很好的发挥了作用  
然后改了一下 希望依次删除字符串中的元素

```
string::iterator it;
    // 错误写法
    for (it = str.begin(); it != str.end(); it++)
    {
        cout << *it << " str: " << str << endl;
        str.erase(it);
    }
```

![错误结果](/images/c++_erase/1.png)

结果出错并且返回异常  
查资料得知 erase 的返回值为被删除迭代器的下一个迭代器  
修改程序

```
// 正确写法
    for (it = str.begin(); it != str.end(); )   // 注意这里去掉了it++
    {
        cout << *it << " str: " << str << endl;
        it = str.erase(it);

    }
```

![正确结果](/images/c++_erase/2.png)

结果无异常
