

# 服务

## 用户服务

- 用户登录
- 用户注册
- 用户基本信息查询
- 无状态（无Session）
- 单点登录

## 课程服务

- 登录验证
- 课程的CURD

## 信息服务

- 发送邮件
- 发送短信

## 用户edgeservice

## 课程edgeservice

## API GATEWAY

反向代理、服务路由



# 3-1 微服务业务分析

## 创建项目

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0301_01.jpg)

- 设置项目名称、存放地点、GroupId和ArtifactId：

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0301_02.jpg)



## 绘制UML图

### 打开工具

链接地址：[ProcessOn](https://processon.com/diagrams)

点击左下角的【更多图形】进行设置：

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0301_03.jpg)

### 绘制图形

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0301_04.jpg)



# 3-2 Thrift安装与验证

在IDEA中通过控制台，用brew安装python

```
brew install python
```

- 安装thrift插件

```
pip install thrift
```

- 最后更新pip版本

```
/Library/Frameworks/Python.framework/Versions/3.8/bin/python3 -m pip install --upgrade pip
```

- 详细log

```
/bin/zsh  /Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/SourceCode/message-thrift-python-service/thrift/gen-code.sh 
coderdream@MacBook-Pro thrift % /bin/zsh  /Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/SourceCode/message-thrift-python-service/thrift/gen-code.sh 
coderdream@MacBook-Pro thrift % brew install pip
Error: No available formula with the name "pip" 
pip is part of the python formula:
  brew install python
coderdream@MacBook-Pro thrift % brew install python
==> Downloading https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/bottles/gdbm-1.18.1.catalina.bottle.1.tar.gz
######################################################################## 100.0%
==> Downloading https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/bottles/readline-8.0.4.catalina.bottle.tar.gz
######################################################################## 100.0%
==> Downloading https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/bottles/sqlite-3.31.1.catalina.bottle.tar.gz
######################################################################## 100.0%
==> Downloading https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/bottles/xz-5.2.5.catalina.bottle.tar.gz
######################################################################## 100.0%
==> Downloading https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/bottles/python-3.7.7.catalina.bottle.tar.gz
######################################################################## 100.0%
==> Installing dependencies for python: gdbm, readline, sqlite and xz
==> Installing python dependency: gdbm
==> Pouring gdbm-1.18.1.catalina.bottle.1.tar.gz
🍺  /usr/local/Cellar/gdbm/1.18.1: 20 files, 602.8KB
==> Installing python dependency: readline
==> Pouring readline-8.0.4.catalina.bottle.tar.gz
==> Caveats
readline is keg-only, which means it was not symlinked into /usr/local,
because macOS provides BSD libedit.

For compilers to find readline you may need to set:
  export LDFLAGS="-L/usr/local/opt/readline/lib"
  export CPPFLAGS="-I/usr/local/opt/readline/include"

==> Summary
🍺  /usr/local/Cellar/readline/8.0.4: 48 files, 1.5MB
==> Installing python dependency: sqlite
==> Pouring sqlite-3.31.1.catalina.bottle.tar.gz
==> Caveats
sqlite is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have sqlite first in your PATH run:
  echo 'export PATH="/usr/local/opt/sqlite/bin:$PATH"' >> ~/.zshrc

For compilers to find sqlite you may need to set:
  export LDFLAGS="-L/usr/local/opt/sqlite/lib"
  export CPPFLAGS="-I/usr/local/opt/sqlite/include"

==> Summary
🍺  /usr/local/Cellar/sqlite/3.31.1: 11 files, 4MB
==> Installing python dependency: xz
==> Pouring xz-5.2.5.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/xz/5.2.5: 92 files, 1.1MB
==> Installing python
==> Pouring python-3.7.7.catalina.bottle.tar.gz
Error: The `brew link` step did not complete successfully
The formula built, but is not symlinked into /usr/local
Could not symlink bin/2to3
Target /usr/local/bin/2to3
already exists. You may want to remove it:
  rm '/usr/local/bin/2to3'

To force the link and overwrite all conflicting files:
  brew link --overwrite python

To list all files that would be deleted:
  brew link --overwrite --dry-run python

Possible conflicting files are:
/usr/local/bin/2to3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/2to3
/usr/local/bin/idle3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/idle3
/usr/local/bin/pydoc3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/pydoc3
/usr/local/bin/python3 -> /Library/Frameworks/Python.framework/Versions/3.8/bin/python3
/usr/local/bin/python3-config -> /Library/Frameworks/Python.framework/Versions/3.8/bin/python3-config
==> /usr/local/Cellar/python/3.7.7/bin/python3 -s setup.py --no-user-cfg install --force --verbose --install-scripts=/usr/local/Cellar/python/3.7.7/bin --install-lib=/usr/local/lib/python3.7/site-packages -
==> /usr/local/Cellar/python/3.7.7/bin/python3 -s setup.py --no-user-cfg install --force --verbose --install-scripts=/usr/local/Cellar/python/3.7.7/bin --install-lib=/usr/local/lib/python3.7/site-packages -
==> /usr/local/Cellar/python/3.7.7/bin/python3 -s setup.py --no-user-cfg install --force --verbose --install-scripts=/usr/local/Cellar/python/3.7.7/bin --install-lib=/usr/local/lib/python3.7/site-packages -
==> Caveats
Python has been installed as
  /usr/local/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
  /usr/local/opt/python/libexec/bin

You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /usr/local/lib/python3.7/site-packages

See: https://docs.brew.sh/Homebrew-and-Python
==> Summary
🍺  /usr/local/Cellar/python/3.7.7: 4,006 files, 61.2MB
==> Caveats
==> readline
readline is keg-only, which means it was not symlinked into /usr/local,
because macOS provides BSD libedit.

For compilers to find readline you may need to set:
  export LDFLAGS="-L/usr/local/opt/readline/lib"
  export CPPFLAGS="-I/usr/local/opt/readline/include"

==> sqlite
sqlite is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have sqlite first in your PATH run:
  echo 'export PATH="/usr/local/opt/sqlite/bin:$PATH"' >> ~/.zshrc

For compilers to find sqlite you may need to set:
  export LDFLAGS="-L/usr/local/opt/sqlite/lib"
  export CPPFLAGS="-I/usr/local/opt/sqlite/include"

==> python
Python has been installed as
  /usr/local/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
  /usr/local/opt/python/libexec/bin

You can install Python packages with
  pip3 install <package>
They will install into the site-package directory
  /usr/local/lib/python3.7/site-packages

See: https://docs.brew.sh/Homebrew-and-Python
coderdream@MacBook-Pro thrift % pip install thrift
Collecting thrift
  Downloading thrift-0.13.0.tar.gz (59 kB)
     |████████████████████████████████| 59 kB 3.5 kB/s 
Requirement already satisfied: six>=1.7.2 in /Users/coderdream/Library/Python/3.8/lib/python/site-packages (from thrift) (1.14.0)
Building wheels for collected packages: thrift
  Building wheel for thrift (setup.py) ... done
  Created wheel for thrift: filename=thrift-0.13.0-cp38-cp38-macosx_10_9_x86_64.whl size=176870 sha256=624284b7e546a155235c2079f370cd7c6304446ef8dfb3c3f4b6ba978c94264f
  Stored in directory: /Users/coderdream/Library/Caches/pip/wheels/0a/52/7e/8054b57725b8f2b9ddbaacb81b271b939681cc03f8231e6ebc
Successfully built thrift
Installing collected packages: thrift
Successfully installed thrift-0.13.0
WARNING: You are using pip version 20.1; however, version 20.1.1 is available.
You should consider upgrading via the '/Library/Frameworks/Python.framework/Versions/3.8/bin/python3 -m pip install --upgrade pip' command.
coderdream@MacBook-Pro thrift % /Library/Frameworks/Python.framework/Versions/3.8/bin/python3 -m pip install --upgrade pip
Collecting pip
  Downloading pip-20.1.1-py2.py3-none-any.whl (1.5 MB)
     |████████████████████████████████| 1.5 MB 16 kB/s 
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 20.1
    Uninstalling pip-20.1:
      Successfully uninstalled pip-20.1
Successfully installed pip-20.1.1
coderdream@MacBook-Pro thrift % 
```

- 类：message-service.py

```python
from message.api import MessageService
from thrift.transport import TSocket
from thrift.transport import TTransport
from thrift.protocol import TBinaryProtocol
from thrift.server import TServer

class MessageServiceHandler:
    def sendMobileMessage(self, mobile, message):
        """
        Parameters:
         - mobile
         - message

        """
        print("sendMobileMessage")
        return True

    def sendEmailMessage(self, email, message):
        """
        Parameters:
         - email
         - message

        """
        print("sendEmailMessage")
        return True

if __name__ == '__main__':
    handler = MessageServiceHandler()
    processor = MessageService.Processor(handler)
    transport = TSocket.TServerSocket("localhost", "9090")
    tfactory = TTransport.TFramedTransportFactory()
    pfactory = TBinaryProtocol.TBinaryProtocolFactory()

    server = TServer.TSimpleServer(processor, transport, tfactory, pfactory)
    print("python thrift server start")
    server.serve()
    print("python thrift server exit")
```

- 运行结果

```
/usr/local/bin/python3.8 /Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/SourceCode/message-thrift-python-service/message/message_service.py
python thrift server start
```

- 检查服务是否正常启动，端口是否打开

```
coderdream@MacBook-Pro thrift-test % netstat -na|grep 9090
tcp6       0      0  ::1.9090               *.*                    LISTEN
coderdream@MacBook-Pro thrift-test %
```

# 3-3 Python开发信息服务

先删除src文件夹，然后创建Python的Module：

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0303_01.jpg)

##    给IDEA安装Python插件

- 进入【Preference...】菜单：

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0303_02.jpg)

- 选择【Plugins】-》【Marketplace】，然后输入【Python】，选择找的的【Python】后，点击【Install】：

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0303_03.jpg)

- 安装完成后即可新建Python类型的New Module了（Module SDK在此之前要先安装）：

![](/Users/coderdream/Documents/04_GitHub/iMooc-Docker-Kubernetes-in-Action/images/Ch03/ch0303_04.jpg)



