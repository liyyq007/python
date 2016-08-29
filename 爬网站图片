#-*- coding:utf-8 -*-
import re     #正则表达式
import requests     #模块
import os     

word = raw_input("输入关键词（英文）,就能自动下载相应的图片，文件保存在d盘同名文件夹下")    #输入
html = 'http://image.baidu.com/search/flip?tn=baiduimage&ie=utf-8&word='+word+'&ct=201326592&v=flip'      #在这个网址找关键词
result = requests.get(html).text                                 #提取，转成Unicode型
pic_url = re.findall('"objURL":"(.*?)",',result,re.S)            #正则表达式，抓取
aa = os.mkdir(r'd:/%s/'%word)                                     #在d盘新建文件夹，名称与输入一致（字符）
i = 1
for each in pic_url:                                             #循环，罗列每个each
    print word + str(i) + each                                    #打印每个图片的网址
    try:                                                          #
        pic = requests.get(each, timeout=10)                         #提取each网址，延迟10以内
    except requests.exceptions.ConnectionError:                      #超时错误，打印错误
        print '【错误】当前图片无法下载'
        continue                                                #跳出

    string = 'd:/%s/'%word+word+str(i)+".jpg"                        #设定图片输入格式
    fp = open(string,'wb')                                         #以写入型打开文件夹
    fp.write(pic.content)                                          #下载pic图片内容，二进制
    fp.close()                                                  
    i += 1
