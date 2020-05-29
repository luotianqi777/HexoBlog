---
title: Python保存网页
date: 2020-05-29 14:04:01
tags:
- Python
---

## 导入所需库
```
import requests
import os
```
## 获取网页内容
```
def getHtml(sub_url):
    baseurl = 'http://www.mzdbl.cn/maoxuan/'
    url = baseurl + sub_url
    print('正在读取: '+url)
    res = requests.get(url=url)
    # 中文编码
    res.encoding = 'GBK'
    if res.status_code==200:
        print('访问成功')
        return res.text.replace('gb2312','utf-8')
    else:
        print('访问错误代码: {0}'.format(res.status_code))
        return None
```
## 保存网页
```
def saveHtml(caption, section):
    if caption == 1:
        sub_url = 'maoxuan{0}/{0}-{1}.htm'.format(caption, section)
    elif caption == 5:
        sub_url = 'maoxuan{0}/{0}-{1}.html'.format(caption, section)
    else:
        sub_url = 'maoxuan{0}/{0}-0{1}.html'.format(caption, section)
    data = getHtml(sub_url)
    if not data == None:
        path = 'maoxuan{0}'.format(caption)
        file_name = path+'/{0}.html'.format(section)
        if not os.path.exists(path):
            os.mkdir(path)
        print('储存到 '+file_name)
        with open(file_name, 'w') as f:
            f.write(data)
            f.close()
        return True
```
## 主函数 保存所需网页
```
if __name__ == "__main__":
    for caption in range(5):
        section = 1
        while True:
            status = saveHtml(caption+1,section)
            if status:
                section+=1
            else:
                break
```