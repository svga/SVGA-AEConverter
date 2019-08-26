# SVGA-AEConverter

本工具适用于 After Effects CC 2018 & 2019，
使用本工具可以将 AEP 文件转换为 SVGA 文件。

## Using
[Usage](./DOC/Usage.md)

## Detail
[Converter](./DOC/Converter.md)

## Intro

SVGA-Converter 是一个 Adobe CEP 插件，
由两个部分组成：
`CEP + JSX`

### CEP

CEP 是一个带 Node 环境的本地 Web 模块，
你可以使用各种前端框架并且最终产生 
HTML + JS + CSS
用于业务功能 UI 展示。

### JSX

JSX 使用 ExtendScript，
可以通过 Adobe 提供的 API 管理插件所在宿主应用的 DOM Tree，
从而通过脚本代码对宿主应用进行操作。
<br><br>

## DEV

### 分支

可以看到目前 Converter 主要的分支有：

#### 0.x

* converter-ae_0.1.x_maint
* converter-ae_0.2.x_maint

#### 1.x

* converter-ae_1.0.0_feature

其中，
`0.1.x `对应的是 1.x 格式的基于 json 格式的 SVGA 动画，
只有一个 svga.jsx 文件，
可以直接在 Extension Toolkit 中运行调试，方便进行纯 JSX 开发。
 
`0.2.x `对应的是 2.x 格式的基于 protobuf 格式的 SVGA 动画。
在 0.1.x 的 jsx 上集成了 HTML 图形界面和 Protobuf 用于支持 2.x,
这两个部分一般不需要改动。

`1.x` 对应的是使用 Vue + js 重构过的插件。
目前正在开发验证中。

### 开发

对 CEP 的开发与前端项目相似，
这里主要讲 JSX 开发。

1. 切换到 0.1.x 分支。
2. 打开项目根目录：
    * 
    * LICENSE ------- ()
    * README.md ----- ()
    * CHANGELOG.md -- ()
    * DEV ----------- (开发)
    * DOC ----------- (文档)


我们在 DEV/source 目录进行开发工作，
并在 DOC 中及时更新特性文档。

开发完成后，使用
```
$ npm i
$ npm run start
```

`./build` 目录就会产生对应的 `svga.jsx` 文件。

### 测试

1. 打开 Extension Toolkit；
2. 打开生成的 svga.jsx 文件；
3. 选择对应宿主软件
![selectSource](media/selectSource.png)



#### 断点
点击即将调试代码左边框：

#### 调试
![debug](media/debug.png)

#### Log

在断点的 Console 窗口输入对应变量，
就可以直接打印信息。

在代码中使用：
`$.writeln(message)`
可以在运行时将对象打印在 Console 窗口上。

### 合并

0.1.x 开发验证完成，
可以将 0.1.x 直接合并到 0.2.0，
为 JSX 代码带上 UI 和 2.x 支持。

### 打包

0.2.0 项目可以生成图形插件的安装包 .zxp 文件，
在 DOC 目录下使用：
```
$ npm i
$ npm run start
```

zxp 文件就会出现在对应 mac | win 文件夹中。


