# 常用包

## pipdeptree, yolk/yolk3k, httpie, django-mail-queue

## selenium

浏览器自动化测试包，通过调用各浏览器开发商提供的驱动进行测试。

Chrome和IE的驱动：

<https://chromedriver.storage.googleapis.com/index.html>

<http://selenium-release.storage.googleapis.com/index.html>

## lettuce & lettuce_webdriver

**lettuce**

python的BDD测试框架，其产生受启发于ruby的cucumber。

**lettuce_webdriver**

lettuce用于调用selenium.webdriver的包。

## nose

python的测试框架，继承自unittest但更容易使用，代码规范也更python（例：assertEqual => assert_equal）

## celery & django-celery

python分布式任务队列，可配合django或者RabbitMq使用。配合django使用时需安装django-celery包。

版本方面需注意以下几点：

1. celery4及以上版本不支持windows
2. celery3.1.25以下版本不支持django1.10及以上
3. django-celery 3.1.17不支持django1.9.2以上，因为django的高版本移除了BaseCommand的option_list，目前可安装开发版解决这个问题。

    	pip install git+https://github.com/celery/django-celery#egg=master

## demjson

可直接转换javascript的object到python的dict的包。

        import demjson

        js_obj = '{x: 1, y: 2, z: 3}'
        py_obj = demjson.decode(js_obj)

# 新奇用法

## pip 源配置

[Ref1](http://topmanopensource.iteye.com/blog/2004853) |

**直接在命令行中指定pipy源**

    pip install web.py -i http://pypi.douban.com/simple

**在pip配置中指定源**

linux下，pip配置文件在`~/.pip/pip.conf`，windows在`%HOMEPATH%\pip\pip.ini`。

    [global]
    timeout = 60
    index-url = http://pypi.douban.com/simple

**pipy国内镜像**

<http://mirrors.aliyun.com/help/pypi>  阿里云

<http://pypi.douban.com/>  豆瓣

<http://pypi.hustunique.com/>  华中理工大学

<http://pypi.sdutlinux.org/>  山东理工大学

<http://pypi.mirrors.ustc.edu.cn/>  中国科学技术大学

## 可编辑安装

    pip install -e  (editable 其过程为源码下载到当前目录，再把源码链接到pip环境，可编辑源码)

## 从github安装

    pip install git+https://github.com/celery/django-celery#egg=master


## ipython配置

**ipython启动时默认加载包**

windows下`%HOMEPATH%\.ipython\profile_default\startup\start.py`

    import os
    import re
    import sys
    import json
    import requests
    from datetime import datetime

# 安装解惑

## Visual C++ for Python 2.7

可使用微软aka服务访问最新的下载页面

<http://www.aka.ms/vcpython27>

## mysql-python

windows上直接用pip安装不成功的可能性较大，在windows上使用pip安装的过程中需要用到c++编译器，所以需要安装Microsoft Visual C++ Compiler for Python。

VC for python2.7:

<https://www.microsoft.com/en-us/download/details.aspx?id=44266>

安装不成功还可以使用预编译的mysql-python：

<http://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python>

### Cannot open include file: 'config-win.h': No such file or directory

[Ref1](http://stackoverflow.com/questions/1972259/cannot-open-include-file-config-win-h-no-such-file-or-directory-while-inst) |
[Ref2](http://www.mamicode.com/info-detail-307184.html) |
[Ref3](http://stackoverflow.com/questions/26866147/mysql-python-install-fatal-error)

1. 下载源码包. <https://pypi.python.org/pypi/MySQL-python/1.2.5> 

2. 检查文件site.cfg中connector的值是否是你安装mysql connector的目录。默认应该是C:\Program Files(x86) \MySQL\MySQL Connector C 6.0.2 (32位)或C:\Program Files\MySQL\MySQL Connector C 6.0.2 (64位)

    修改为你安装的目录即可. 

3. python setup.py install

### 使用pip安装mysql-python总是不成功

mysql-python在pip下安装不成功的话可以试试用easy_intall安装
    
    easy_install MySQL-python
