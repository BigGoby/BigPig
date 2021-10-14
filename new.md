# 将自己的Python包发布到Pypi

## 1.创建一个Git仓库(GitHub/Gitee)
![](../images/1.jpg)
![Image text](https://github.com/BigGoby/BigPig/blob/main/images/1.jpg)
> 代码库创建完成后,通过git clone到本地 

## 2.编写测试用例代码
> a.创建BigPig包
![](../images/1.2.jpg) 
![Image text](https://github.com/BigGoby/BigPig/blob/main/images/1.2.jpg)

> b.编写测试代码  
![](../images/2.jpg)
![Image text](https://github.com/BigGoby/BigPig/blob/main/images/2.jpg)

## 3.创建setup.py和LICENSE文件
![](../images/3.jpg)
![Image text](https://github.com/BigGoby/BigPig/blob/main/images/3.jpg)

> + setup.py 包描述文件
```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
# @Time : 2021/10/12 6:00 下午
# @Author : A Big Boby
# @File : setup.py.py 
# @Software: PyCharm


import setuptools

with open('README.md', 'r', encoding='utf-8') as fh:
    long_description = fh.read()

setuptools.setup(
    name='whrtest',
    version='0.0.1',
    author='A Big Boby',
    author_email='ilikepython@163.com',
    description='Oh! whr',
    long_description=long_description,
    url='https://github.com/BigGoby/BigPig',
    packages=setuptools.find_packages(),
    classifiers=[
        'Programming Language :: Python :: 3',
        'License :: OSI Approved :: MIT License',
        'Operating System :: OS Independent',
    ],
)
```
> 参数解释

![](../images/28c248f3.png)
![Image text](https://github.com/BigGoby/BigPig/blob/main/images/28c248f3.png)


> + LICENSE
```
Copyright (c) 2021 xiaoxiong Authors. All Rights Reserve.

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
## 4.注册pypi账号,安装模块
> a.首先需要注册pypi账号
> pypi测试地址：https://test.pypi.org/
> pypi正式包地址: https://pypi.org/
> $\color{FF0000}{注意！测试环境与正式环境账号不互通,账号注册成功后需要验证邮箱,否则无法正常提交}$    

> b.执行vim ~/.pypirc
```
[distutils]
index-servers =
  pypi
  pypitest

[pypitest]
repository: https://testpypi.python.org/pypi/
username: xxx 
password: xxx

[pypi]
repository = https://upload.pypi.org/legacy/
username = xxxx
password = xxxx
```

>$\color{FF0000}{注意！此步不执行会导致后面同步pypi出现403错误}$    


> c.切换到你的虚拟环境安装如下包
```
python3 -m pip install --upgrade setuptools wheel
python3 -m pip install --upgrade twine
```
## 5.对你的项目进行打包
> a.直接推送到pypi正式环境
> python3 setup.py sdist bdist_wheel

> b.执行中如图所示
> ![](../images/4.jpg)
> ![Image text](https://github.com/BigGoby/BigPig/blob/main/images/4.jpg)

> c.执行完成后,你的项目目录会变成
> ![](../images/5.jpg)
> ![Image text](https://github.com/BigGoby/BigPig/blob/main/images/5.jpg)

> 会生成build,dist,xx.egg-info文件夹,其中库版本存在dist中,上传时会按照版本低->高逐步检查上传
> 

## 6.发布
```
twine upload dist/*
```

> 出现以下连接就发布成功了
> ![](../images/8.jpg)
> ![Image text](https://github.com/BigGoby/BigPig/blob/main/images/8.jpg)


> 发布成功后可以在pypi官网查看到
> ![](../images/11.jpg)
> ![Image text](https://github.com/BigGoby/BigPig/blob/main/images/11.jpg)
> 

## 7.测试
> a.进入你的虚拟环境,使用pip install xxx 安装你刚才发布的库
> ![](../images/9.jpg)
> ![Image text](https://github.com/BigGoby/BigPig/blob/main/images/9.jpg)

> b.显示安装成功后,启动python查看包是否可用
> ![](../images/10.jpg)
> ![Image text](https://github.com/BigGoby/BigPig/blob/main/images/10.jpg)
> 
# Over！大功告成！