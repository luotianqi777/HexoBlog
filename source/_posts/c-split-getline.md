---
title: c++实现split(通过getline)
date: 2019-07-12 21:51:53
tags:
  - C++
  - Compete
---

众所周知  
c++中 string 没有自带的 split 函数(亏你还是老大哥)  
网上关于 split 函数的优秀写法很多  
本人不再赘述  
近几日翻 C++API 时发现了 getline 一个有趣的方法

```
istream& getline (istream& is, string& str, char delim);
```

第一个参数是一个输入流，第二个参数是一个对字符串的常引用，第三个参数是分割符  
在读入时遇到分割符则停止  
可以用这个来实现单分割符的 split 功能

```
#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main() {
    stringstream input("45,65,45231,4646,4564");
    string str;
    while (getline(input, str, ',')) {
        cout << str << endl;
    }
    return 0;
}
```

![](/images/c++_split_getline/1.png)

简单方便快速。
