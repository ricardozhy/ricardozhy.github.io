---
layout: post
title: 爬取原神同人社的pljj照片
slug: genshin
date: 2021-04-24 16:40
status: publish
author: 华仔仔
categories: 
  - python
tags: 
  - python
  - 爬虫
excerpt: 爬取原神同人社的pljj照片

---


最近在学习python，然后看了我室友最近在看小说，就先看了几篇文章，然后爬了本他正在看的小说练练手。然后就有了这篇爬取原神同人社的pljj的照片，第一次写博客，大家多包涵包涵鸭！

欢迎交流GitHub：Ricardo-Zzhao @[https://github.com/Ricardo-Zzhao](https://github.com/Ricardo-Zzhao)

邮箱：ricardoz_y@qq.com

博客：[Ricardoz's Site](https://ricardozhy.github.io/)

## 1.首先导入相关的模块

```python
import jsonpath
import requests
import os
import json
```


## 2.页面分析

先打开[米游社·原神](https://bbs.mihoyo.com/ys/home/29?type=hot)
![](https://img-blog.csdnimg.cn/20210423222301524.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1JpY2FyZG9zeWc=,size_16,color_FFFFFF,t_70)
找到热门部分，**右击检查，network，ctrl+f8之后点击多回蓝色箭头**，找到下面接口，接口带有getForumPostList，请求拿到数据。
![](https://img-blog.csdnimg.cn/20210423223314224.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1JpY2FyZG9zeWc=,size_16,color_FFFFFF,t_70)
![](https://img-blog.csdnimg.cn/20210423223327205.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1JpY2FyZG9zeWc=,size_16,color_FFFFFF,t_70)


请求网站获取数据

```python
headers ={
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36'
		}
#构造请求头，把爬虫程序伪装成正常的浏览器用户
if not os.path.exists('./原神images'):
    os.mkdir('./原神images/')
#创建保存图片的文件夹

url='https://bbs-api.mihoyo.com/post/wapi/getForumPostList?forum_id=29&gids=2&is_good=false&is_hot=true&page_size=20'
```

获取网页参数
![](https://img-blog.csdnimg.cn/20210424001944321.png)

```python
param = {
            'forum_id': '29',
            'gids': '2',
            'last_id': image_id,
            'page_size': '20'
            }
```

last_id: 代表这个数据最后一张图片相对于整个页面图片的位置编号
page_size: 代表这个数据总共有多少个图片



## 3.解析数据

```python
response = requests.get(url=url, headers=headers, params=param)
    response.encoding = response.apparent_encoding
    #使python编码方式自动变化
    print(response.status_code)
    #输出status_code，观察网页变化
    response = response.text
    json_data=json.loads(response, strict=False)
    #把字符串转换成json数据
    image_url= jsonpath.jsonpath(json_data, '$..images')
    #使用jsonpath解析数据，获取所有图片的url，返回的是一个列表
    print(image_url)
```

因为requests的时候发现它是一个字典，可以使用Python中的键值索引方式获取到想要的数据，但这里使用了jsonpath解析数据，能够更快捷的获取想要的数据

 

```python
   for i in image_url:
        #遍历拿到每一个URL
        for img in i:
            page_url=img
            image_data = requests.get(page_url).content
            #使用requests请求图片URL，获取图片数据
```

使用requests请求每张图片URL，获取图片数据

## 4.数据保存

```python
with open(image_path, 'wb') as f:
    f.write(image_data)
    print(image_name, '下载完毕！！！')
```

## 5.成果展示

![](https://img-blog.csdnimg.cn/20210424003242887.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1JpY2FyZG9zeWc=,size_16,color_FFFFFF,t_70)
爬取成功啦！

## 6.完整代码

```python
import jsonpath
import requests
import os
import json

path='./原神images'
page = input('请输入您想要爬取的页数：')
page = int(page) + 1
n=0
headers ={
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36'
}
#构造请求头，把爬虫程序伪装成正常的浏览器用户
if not os.path.exists('./原神images'):
    os.mkdir('./原神images/')
#创建保存图片的文件夹

url='https://bbs-api.mihoyo.com/post/wapi/getForumPostList?forum_id=29&gids=2&is_good=false&is_hot=true&page_size=20'
# 资源包的url链接

image_id = 0
for m in range(1, page):
    param = {
            'forum_id': '29',
            'gids': '2',
            'last_id': image_id,
            'page_size': '20'
            }

    response = requests.get(url=url, headers=headers, params=param)
    response.encoding = response.apparent_encoding
    #使python编码方式自动变化
    print(response.status_code)
    #输出status_code，观察网页变化
    response = response.text
    json_data=json.loads(response, strict=False)
    #把字符串转换成json数据
    image_url= jsonpath.jsonpath(json_data, '$..images')
    #使用jsonpath解析数据，获取所有图片的url，返回的是一个列表
    print(image_url)
    for i in image_url:
        #遍历拿到每一个URL
        for img in i:
            page_url=img
            image_data = requests.get(page_url).content
            #使用requests请求图片URL，获取图片数据
            image_name='{}'.format(n+1) + '.jpg'
            image_path = path + '/' + image_name
            with open(image_path, 'wb') as f:
                f.write(image_data)
                print(image_name, '下载完毕！！！')
            n += 1
        image_id += 20
```


## 7.经验感想

今天是第一次写一篇博客，之前一直听说爬虫一项很厉害的技术，正好这学期学了python，就想着什么时候能够爬取一些东西。然后就去看了好几篇大佬的博客，这些代码有很多借鉴他们的地方，在这里想记录一点自己再互联网上留下的记忆，可能很多年过后，想起来自己还写过这样一篇博客。学习计算机我觉得真的要有很浓厚的兴趣，就像现在在学Hadoop，flume，hbase，hive等等，能记录下学习的过程，我觉得真的是一件很美好的事情。要是写的还不错记得点赞，关注，收藏，一键三连啦！阿里嘎多，米娜桑哇！

**Author：RicardoZ 
CSDN：https://blog.csdn.net/Ricardosyg**
