# UdonSharp

## 将 C# 编译成 Udon 程序集的编译器

UdonSharp 是一种将 C# 编译为 Udon 程序集的编译器。UdonSharp 目前并不符合任何版本的 C# 语言规范，因此有许多内容无法实现或无法运行。

## 所支持的 C# 功能
- 流程控制
    - 支持: `if` `else` `while` `for` `do` `foreach` `switch` `return` `break` `continue` `ternary operator (condition ? true : false)` `??`
- 隐式和显式类型转换
- 数组和数组索引器
- 所有内置的算术运算符
- 条件短路 `(true || CheckIfTrue())` 不会执行 CheckIfTrue()
- `typeof()`
- 带有 out 或 ref 参数的外部方法（如 `Physics.Raycast()` 的许多变体）
- 带有参数和返回值的用户自定义方法，支持 out/ref、扩展方法和 `参数`。
- 用户自定义属性
- 静态的用户方法
- UdonSharpBehaviour 继承、虚拟方法等。
- Unity/Udon 事件回调带有参数。例如，使用 VRCPlayerApi 参数注册 OnPlayerJoined 事件是有效的。
- 字符串内插
- 字段初始化函数
- 交错数组
- 引用其他自定义 UdonSharpBehaviour 类、访问字段并调用相关方法
- 通过 `[RecursiveMethod]` 属性支持递归方法调用

## 与普通 Unity C# 的不同之处
- 要获得制作 UdonSharp 脚本的最佳体验，请让您的脚本继承自 `UdonSharpBehaviour` 而不是 `MonoBehaviour` 。
- 如果您需要调用 `GetComponent<UdonBehaviour>()`，您目前需要使用 `(UdonBehaviour)GetComponent(typeof(UdonBehaviour))` 来调用，因为 UdonBehaviour 尚未公开通用获取组件方法。不过，`GetComponent<T>()` 可用于其他 Unity 组件类型。
- Udon 目前只支持数组 `[]` 集合，因此 UdonSharp 目前也只支持数组。可能会在将来某个时候支持 `List<T>`，但目前还不支持。
- 字段初始化器在编译时进行求值，如果有任何依赖于场景中其他对象的初始化逻辑，你应该在 Start 方法中进行这些初始化。
- 在字段上使用 `UdonSynced` 属性来同步它们。
- 由于 UdonVM 的限制，数值转换会检查溢出。
- 变量的内部类型由 `.GetType()` 返回时，不一定总是与预期相符，因为 U# 会抽象某些类型以便在 Udon 中工作。例如，任何交错数组类型将返回 `object[]` 类型，而不是类似 `int[][]` 这样的 2D int 交错数组类型。

## 影响 U# 的 Udon bugs
- 在结构体上调用变异方法不会修改该结构体（例如，对 Vector3 调用 Normalize() 方法）。 https://vrchat.canny.io/vrchat-udon-closed-alpha-bugs/p/raysetorigin-and-raysetdirection-not-working

## 开始

### 依赖
- Unity 2019.4.31f1
- [VRCSDK3 + UdonSDK](https://vrchat.com/home/download)
- 最新 UdonSharp [发行版](https://github.com/vrchat-community/UdonSharp/releases/latest)

### 安装
1. 阅读 Udon 入门文档页面 /docs.vrchat.com/docs/getting-started-with-udon，这里有 Udon 的基本安装说明。
2. 安装在入门页面上链接的最新版本的 VRCSDK3。
3. 从 [这里](https://github.com/vrchat-community/UdonSharp/releases/latest) 获取最新的 UdonSharp 发行版并将它安装进您的项目里。

### 入门
1. 在您的场景里创建一个新的 Object
2. 为您的 Object 添加 `Udon Behaviour` 组件
3. 在 “New Program” 按钮下方，点击下拉菜单，并选择 “Udon C# Program Asset”
4. 现在点击 “New Program” 按钮，这将为您创建一个新的 UdonSharp 程序资源
5. 点击 “Create Script” 按钮，选择一个保存位置并命名您的脚本。
6. 这将创建一个模板脚本，准备让您开始工作。打开您选择的编辑器，并开始编程

#### 在资产浏览器里创建资产

如果您不想从 UdonBehaviour 创建资产，您也可以按照以下方式创建资产：
1. 在您的资产浏览器里右键
2. 选择 Create > U# script
3. 点击 U# script, 这会打开一个创建资产的对话框
4. 命名您的脚本并点击 Save 保存
5. 这会创建一个 .cs 脚本文件和一个 UdonSharp 程序资产（在同目录下）

### 示例脚本

#### 旋转方块演示

这会使其附加到的对象每秒旋转90度。

```cs
using UnityEngine;
using UdonSharp;

public class RotatingCubeBehaviour : UdonSharpBehaviour
{
    private void Update()
    {
        transform.Rotate(Vector3.up, 90f * Time.deltaTime);
    }
}
```

#### 其他示例

要查看更多示例，请访问 [示例](https://github.com/Merlin-san/UdonSharp/wiki/examples) 页面, Examples 文件夹也包含了 U# 脚本, 或者访问 [社区资源](https://github.com/Merlin-san/UdonSharp/wiki/community-resources) 页面。

## 致谢

- [CONTRIBUTORS.md](https://github.com/vrchat-community/UdonSharp/blob/master/CONTRIBUTORS.md) 列出了帮助改进 UdonSharp 的人们
- 开源项目 [Harmony](https://github.com/pardeike/Harmony) 帮助 Udonsharp 提供更好的编辑器体验


# 
[![Discord](https://img.shields.io/badge/Discord-Merlin%27s%20Discord%20Server-blueviolet?logo=discord)](https://discord.gg/Ub2n8ZA)
