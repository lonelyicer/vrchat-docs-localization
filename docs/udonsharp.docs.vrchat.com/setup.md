# 开始

**依赖**
- [Unity 2019.4.31f1](https://unity3d.com/get-unity/download/archive)
- [VRCSDK3 + Udon](https://vrchat.com/home/download)

**安装**

您可以通过 [VRChat Creator Companion](https://vcc.docs.vrchat.com/) (简称 VCC), 以及它的 [命令行](https://vcc.docs.vrchat.com/vpm/cli/) 版本, 或者 [初学者模板](https://github.com/vrchat-community/template-udonsharp) 来获取 UdonSharp。

## 通过 VCC 创建新的 UdonSharp 项目：
- 安装最新版的 [Creator Companion](https://vrchat.com/home/download)。
- 在主屏幕点击 "New", 然后选择 "UdonSharp", 并选择一个目录。
- 点击 "Open Project"。 就这样完成啦!

## 通过源码控制创建新的 UdonSharp 项目：
- 访问 [UdonSharp 项目模板仓库](https://github.com/vrchat-community/template-udonsharp)。
- 点击 "Use this template"。
- 使用你最喜欢的 Git 客户端克隆项目到你的电脑。
- 直接使用 Unity 打开项目, 或者将其添加至 VCC 以方便后续升级。

## 为已有的 Udon 项目安装 UdonSharp：
- 将项目添加至VCC，如果可以请将其迁移到最新版本。
- 在项目列表页面中选中项目。
- 在软件包列表上方的仓库下拉菜单中，请确保选择了 "Curated"。
![image](/udonsharp.docs.vrchat.com/images/repos-official-curated.png)
- 在软件包列表中找到 UdonSharp 并点击 "Add"。


## 通过命令行客户端创建或添加 UdonSharp
[命令行客户端](https://vcc.docs.vrchat.com/vpm/cli/) 专为高级用户设计，同时它也是在无视图操作系统中管理 VPM 仓库的最佳工具
- [从模板创建项目](https://vcc.docs.vrchat.com/vpm/cli/#new)
- [为项目安装软件包](https://vcc.docs.vrchat.com/vpm/cli/#add-package)

**入门**

1. 在您的场景里创建一个新的 Object
2. 为您的 Object 添加 `Udon Behaviour` 组件
3. 在 “New Program” 按钮下方，点击下拉菜单，并选择 “Udon C# Program Asset”
4. 现在点击 “New Program” 按钮，这将为您创建一个新的 UdonSharp 程序资源
5. 点击 “Create Script” 按钮，选择一个保存位置并命名您的脚本。
6. 这将创建一个模板脚本，准备让您开始工作。打开您选择的编辑器，并开始编程

**在资产浏览器里创建资产**

如果您不想从 UdonBehaviour 创建资产，您也可以按照以下方式创建资产：
1. 在您的资产浏览器里右键
2. 选择 Create > U# script
3. 点击 U# script, 这会打开一个创建资产的对话框
4. 命名您的脚本并点击 Save 保存
5. 这会创建一个 .cs 脚本文件和一个 UdonSharp 程序资产（在同目录下）
