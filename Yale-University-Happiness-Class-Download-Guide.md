# Windows 10 环境下载耶鲁大学免费幸福课操作指南

# 1.安装chocolatey

## 0.Chocolatey是什么？

Chocolatey是一种软件管理解决方案，与您在Windows上经历过的任何其他事情都不一样。Chocolatey引入了真正的包管理概念，使您可以对事物进行版本控制，管理依赖关系和安装顺序，更好的库存管理以及其他功能。它是Windows 7+的社区系统打包程序管理器。（非常类似于OS X上的Homebrew。）

## 步骤1

1.以管理员身份运行Windows PowerShell，必须确保[Get-ExecutionPolicy]不受限制。我们建议使用`Bypass`绕过策略来安装东西或`AllSigned`提高安全性。

![](.\images\image-20200331144122018.png)
## 步骤2
2.运行`Get-ExecutionPolicy`。如果返回`Restricted`，则运行`Set-ExecutionPolicy AllSigned`或`Set-ExecutionPolicy Bypass -Scope Process`。

![image-20200331144808763](.\images\image-20200331144808763.png)
## 步骤3
3. 输入选择 A（全是）

## 步骤4
4.运行如下命令

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

![image-20200331145124379](.\images\image-20200331145124379.png)

等待几秒钟后运行结束。。。
##  步骤5
5.如果没有看到任何Error，则可以使用Chocolatey！键入`choco`或`choco -?`，进行验证。

![image-20200331145304329](.\images\image-20200331145304329.png)

# 2 使用chocolatey安装python3

安装Python 3非常简单，因为Chocolatey将Python 3推为默认设置。

## 步骤1

1.运行choco install python后，您应该能够直接从控制台启动Python。（Chocolatey很棒棒，它会自动将Python添加到您的环境变量Path中，以便你后续可以直接在任何地方使用python命令）

![image-20200331150129130](.\images\image-20200331150129130.png)

## 步骤2

2.输入Y或者A，输入Y回车后还需要输入多个Y继续安装，输入A，一次全搞定。

![image-20200331150406150](.\images\image-20200331150406150.png)

## 步骤3

3.等候执行完毕，则安装成功

![image-20200331150442736](.\images\image-20200331150442736.png)

## 步骤4

4.关闭Windows PowerShell窗口重新打开

![image-20200331150733923](.\images\image-20200331150733923.png)

## 步骤5

5.输入python --version命令，得到如下输出，则验证安装成功。

![image-20200331150958128](.\images\image-20200331150958128.png)

# 3.安装三个很有用的setuptools，pip和wheel第三方python软件包

它们使您可以通过一个命令下载，安装和卸载任何兼容的Python软件产品。它还使您只需很少的工作就可以将此网络安装功能添加到自己的Python软件中。

尽管`pip`仅一个就可以从预置的二进制归档文件进行安装，但最新的`setuptools`和`wheel`项目副本对于确保您也可以从源归档文件进行安装很有用。

执行如下三个命令：

安装pip命令：python -m pip install -U pip 

验证pip安装成功命令：pip --version

保持pip，setuptools和wheel最新的更新命令：python -m pip install --upgrade pip setuptools wheel

![image-20200331151639026](.\images\image-20200331151639026.png)

# 4.安装coursera-dl

## 步骤1

1.执行pip install coursera-dl命令安装coursera-dl

![image-20200331162457137](.\images\image-20200331162457137.png)

# 5. 安装EditThisCookie 扩展程序，在chrome中进行搜索

安装过程简单（略），其实找这个程序在google商店是找不到的，要在google里搜索才可以，如果无法连接google的同学，自行想办法咯。

#6.注册coursera-dl账号并登陆

注册和登陆过程比较简单（略）

# 7.使用EditThisCookie获取CAUTH值

直接看图：

![image-20200331162024753](.\images\image-20200331162024753.png)

# 8.设置hosts文件映射

国内就是这么麻烦，下载视频时遇到问题，可以在主机文件（C：/Windows/drivers/etc/ hosts）中添加“ 52.84.167.78 d3c33hcgiwev3.cloudfront.net”，并使用“ ipconfig / flushdns”刷新DNS。

![image-20200331161458195](.\images\image-20200331161458195.png)

![image-20200331161427684](.\images\image-20200331161427684.png)

至此，您的环境已经OK了，可以批量去下载课程了。。。这看起来如此简单的事情，就是需要这么折腾才可以完成。

# 9.下载课程

使用cd命令进入你想要下载课程的文件夹目录候再执行

coursera-dl -u <yourUserName> -p <yourPassword> the-science-of-well-being -ca <yourCookieCAUTH>

其中yourUserName就是你注册的账号，yourPassword是你的登陆密码，yourCookieCAUTH是通过EditThisCookie获取到的CAUTH的值，这里不暴漏个人信息就不截图了。

敲完命令，回车，等候你的课程下载完成吧~~具体花费时间和自身所处网络环境有关。

