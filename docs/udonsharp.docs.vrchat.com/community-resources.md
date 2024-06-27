# 社区资源

## 教程和其他信息

### はつぇさん 的博客
- [U# 入門 ①](https://hatuxes.hatenablog.jp/entry/2020/04/05/013310)
- [U# 入門 ②](https://hatuxes.hatenablog.jp/entry/2020/04/05/013323)
- [U# 入門 ③](https://hatuxes.hatenablog.jp/entry/2020/04/05/013336)
- [U# 入門 おまけ](https://hatuxes.hatenablog.jp/entry/2020/04/05/013348)

### やぎりさん 的博客
- [UdonSharp走り書きメモ.cs（執筆中、順次更新）](https://yagiri000.hatenablog.com/entry/2020/04/04/162312)

### Vowgan 的教程视频

这些视频前半部分从 Udon Graph 开始，后半部分涉及 U#
- [VRChat Udon Tutorial | Basic Buttons](https://www.youtube.com/watch?v=GWv3zloRWY4)
- [VRChat Udon Tutorial | Contextual Buttons](https://www.youtube.com/watch?v=01a5qO60qlo)
- [VRChat Udon Tutorial | Jumping and PlayerMods](https://www.youtube.com/watch?v=OventaglGCY)

## 工具
### orels1's UdonToolKit
为您的 U# Behaviours 提供了许多有用的实用行为，并为创建自定义检视器提供了更强大的属性系统。

https://github.com/orels1/UdonToolkit/

### cannorin's extern search
这个工具现在已经相当过时，因为节点注册表有一段时间没有更新了。
这是一个网络工具，可以让您搜索 Udon 可用的函数。
https://7colou.red/UdonExternSearch/

### CyanEmu
CyanEmu 是一个 VRChat 客户端模拟器，允许您直接在 Unity 中测试和调试您的 Udon（SDK2）VRChat 世界。它配备了一个PC玩家控制器，可以进行交互、抓取物品、坐在椅子上、回到出生点等操作。

https://github.com/CyanLaser/CyanEmu

### Phasedragon's Input table

这个表列出了 VRChat 目前绑定的所有输入以及它们如何与每个 VR 控制器配合工作。返回 true 或 false 的输入可以使用 `Input.GetButton()` 和列出的输入名称进行读取。返回在 -1 到 1 或 0 到 1 范围内的输入可以使用 `Input.GetAxis()` 或 `Input.GetAxisRaw()` 进行读取。

https://docs.google.com/spreadsheets/d/1_iF0NjJniTnQn-knCjb5nLh6rlLfW_QKM19wtSW_S9w/edit#gid=1150012376

如果您想测试不在列表上的控制器，可以前往我的输入测试世界

https://vrchat.com/home/world/wrld_f8d5f7e4-185c-4b82-8ecb-8ae0c7953085

### Shatoo's Udon editor debug 
提供一个用户界面来调用带参数的内置事件

https://shatoo.booth.pm/items/1958756

### Jordo's Haptics Testing world
提供三个滑块来调整触觉反馈，并测试它们的感觉，以便稍后在您的代码中使用。

https://vrchat.com/home/launch?worldId=wrld_7f010f63-7a82-4668-b1a5-412b57fb08f5&instanceId=0
