# 配置

所有设置都可以在 `Edit > Project Settings > Udon Sharp` 找到

![Udon Sharp 设置](/udonsharp.docs.vrchat.com/images/udon-sharp-settings.png)

# Udon Sharp

### Auto compile on modify
开启这个选项后脚本将在被修改并保存后自动编译。

### Compile all script
编译包括没有检测到任何修改的 U# 脚本在内的所有脚本。

### Compile on focus
只编译在编辑器获得了焦点并且进行了更改的脚本。

### Script template override
您可以定义自己的自定义模板，用于创建 U# 脚本时使用。
这可以通过将脚本拖放到 `Script template override` 字段中来完成，这样在创建新的 U# 脚本时将使用该模板。

`<TemplateClassName>` 可以根据您给定的文件名来设置类名。

**默认模板**
```cs
using UdonSharp;
using UnityEngine;
using VRC.SDKBase;
using VRC.Udon;

public class <TemplateClassName> : UdonSharpBehaviour
{
    void Start()
    {
        
    }
}
```

# Debugging

### Debug build
启用或禁用 `Inline Code` 和 `Listen for client exceptions`

### Inline Code
在生成的程序集代码中包含 C# 内联代码。

### Listen for client exceptions
这将监听 VRChat 客户端输出日志中的异常，然后尝试将其与项目中的脚本进行匹配。

[在这里获取更多设置帮助](https://github.com/vrchat-community/UdonSharp/wiki/class-exposure-tree)