# cmweb

## 虚拟环境

### Linux

#### 创建

```bash
    $mkdir myproject
    $cd myproject
    $python3 -m venv venv
```

#### 激活

```bash
    $. venv/bin/activate
```

### windows

#### 创建

```bash
$ mkdir myproject
$ cd myproject
$ py -3 -m venv venv

or

$ python2 -m virtualenv venv

> \Python27\Scripts\virtualenv.exe venv
```

#### 激活

```bash
> venv\Scripts\activate
```

然后，pip 安装需要的安装包

## pip自动生成和安装requirements.txt

```bash
生成requirements.txt文件

pip freeze > requirements.txt

安装requirements.txt依赖

pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

pip install -r requirements.txt

OR

pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```

## start first app

```bash
django-admin startproject HelloWorld

python3 manage.py runserver 0.0.0.0:8000
```

## 模型

```bash

sudo apt-get install libmysqlclient-dev

pip install mysqlclient
```

### 数据库配置

```bash
HelloWorld/HelloWorld/settings.py: 文件代码：

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',  # 或者使用 mysql.connector.django
        'NAME': 'test',
        'USER': 'test',
        'PASSWORD': 'test123',
        'HOST':'localhost',
        'PORT':'3306',
    }
}

```

### 定义模型

`Django规定，如果要使用模型，必须要创建一个app。我们使用以下命令创建一个 TestModel 的 app:`

```bash
django-admin startapp TestModel
```

```bash
HelloWorld/TestModel/models.py: 文件代码


# models.py
from django.db import models

class Test(models.Model):
    name = models.CharField(max_length=20)

```

```bash
在settings.py中找到INSTALLED_APPS这一项

INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'TestModel',               # 添加此项
)
```

### 命令行

```bash
$python manage.py migrate   # 创建表结构

$python manage.py makemigrations TestModel  # 让 Django 知道我们在我们的模型有一些变更
$python manage.py migrate TestModel   # 创建表结构
```

## 使用管理工具

启动开发服务器，然后在浏览器中访问 `http://127.0.0.1:8000/admin/`

通过命令 `python manage.py createsuperuser` 来创建超级用户

```bash
# python manage.py createsuperuser
Username (leave blank to use 'root'): zhaofs0921
Email address: kunpeng.zhao@163.com
Password:
Password (again):
Superuser created successfully.
[root@solar HelloWorld]#
```
