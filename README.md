
#### Scoop是什么？


Scoop 是一个基于 Windows 的包管理器，能够帮助开发者高效管理开发环境和应用程序。


它推荐通过命令行进行包的安装、更新和卸载，同时提供了简单易用的包组织方式，透明化了安装和管理的过程。


与传统的 Windows 应用安装比较，Scoop 允许用户使用命令行将应用安装到用户的个人目录中，消除了系统管理员权限的需求。


来看看我本地安装的应用。


![](https://img2024.cnblogs.com/blog/1033233/202412/1033233-20241226194054802-733507570.png)


#### 安装Scoop


透过以下命令安装



```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

#### Scoop的几个核心概念


##### **Bucket (桶)**


Bucket 是 Scoop 中用于存储应用包配置文件 (如 JSON 文件) 的地方。举一个例，`main` 是 Scoop 默认的主 Bucket，还有丰富的社区共享 Bucket，如 `extras`，包含了更多的应用。 添加新的 Bucket：



```
scoop bucket add extras
```

##### **App (应用)**


App 是 Scoop 的核心，它指的是安装和管理的应用程序，比如 Python，.NET，Node.js等。


##### **程序根目录**


Scoop 通常将应用安装在 `~/scoop/apps/` 目录中，便于用户进行独立管理。可以通过以下命令查看安装路径：



```
scoop prefix -name>

```

##### **Version (版本管理)**


Scoop 支持同一应用的多版本管理，通过切换功能可以随时切换用户需要的版本。


#### 多版本管理的原理


Scoop 的多版本管理通过应用根目录中的不同子目录实现，每个版本都保存在独立的目录中：



```
~/scoop/apps//

```

通过设置连接 (如 `current` 连接)，Scoop 可以日常指导到指定版本：



```
~/scoop/apps//current -> 

```

这样，用户可以随时切换版本，而不需要重新安装。


#### 怎么安装包：以 .NET 和 Python 举例


##### **安装 version**


透过 Scoop 安装 versions，versions用来管理旧版本的应用：



```
scoop bucket add version

```

##### **安装 .NET**


透过 Scoop 安装 .NET：



```
scoop install dotnet-sdk

```

验证安装：



```
dotnet --version

```

##### **安装两个版本的 .NET**


安装特定版本：



```
scoop install dotnet6-sdk
scoop install dotnet7-sdk

```

切换版本：



```
scoop reset dotnet6-sdk
scoop reset dotnet7-sdk

```

##### **安装 Python**


透过 Scoop 安装 Python：



```
scoop install python

```

验证安装：



```
python --version

```

##### **安装两个版本的 Python**


安装特定版本：



```
scoop install python27
scoop install python310

```

切换版本：



```
scoop reset python27
scoop reset python310

```

#### 


#### Scoop 的更新操作


##### **更新 Scoop 自身**


使用以下命令更新 Scoop：



```
scoop update

```

##### **更新所有已安装的包**


更新所有已安装包到最新版本：



```
scoop update *

```

##### **更新特定的包**


如果只需要更新某个特定包，例如 Python：



```
scoop update python

```

#### 


#### 常见配置和问题解决


##### **设置全局安装路径**


如果需要为所有用户配置全局安装路径，可以修改 Scoop 的配置：



```
scoop config global_path true

```

##### **环境变量冲突**


切换不同版本的应用时，可能会遇到环境变量冲突。通过以下命令重置环境变量：



```
scoop reset -name>

```

##### **清理过时版本**


清理应用的旧版本以节省磁盘空间：



```
scoop cleanup -name>

```

#### 


#### 通过 Scoop 快速搭建开发环境


利用 Scoop，可以快速搭建一个开发环境。例如：


##### 安装 VS Code



```
scoop install vscode

```

##### 安装 Node.js



```
scoop install nodejs

```

##### 安装 Git



```
scoop install git

```

通过这些简单的命令，您可以快速构建一个功能齐全的开发环境。


![](https://images.cnblogs.com/cnblogs_com/chenyishi/1348350/o_240408130234_wx.png) 本博客参考[milou云加速器cloud](https://www.huabeikeji.com)。转载请注明出处！
