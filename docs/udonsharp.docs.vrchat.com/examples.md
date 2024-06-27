# 示例

* [旋转方块](#旋转方块)
* [玩家设置](#玩家设置)
* [交互](#交互)
* [传送玩家](#传送玩家)
* [获取玩家](#获取玩家)
* [UdonSharp 脚本示例](#udonsharp-脚本示例)


---

### 旋转方块
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

### 玩家设置
```cs
using UnityEngine;
using UdonSharp;
using VRC.SDKBase;

public class PlayerModSettings : UdonSharpBehaviour
{
    VRCPlayerApi playerApi;

    [Header("Player Settings")]
    [SerializeField] float jumpImpulse = 3;
    [SerializeField] float walkSpeed = 2;
    [SerializeField] float runSpeed = 4;
    [SerializeField] float gravityStrengh = 1;

    void Start()
    {
        playerApi = Networking.LocalPlayer;
        playerApi.SetJumpImpulse(jumpImpulse);
        playerApi.SetWalkSpeed(walkSpeed);
        playerApi.SetRunSpeed(runSpeed);
        playerApi.SetGravityStrength(gravityStrengh);
    }
}
```
更高级的示例位于 [UdonSharp的示例文件夹](https://github.com/Merlin-san/UdonSharp/blob/master/Assets/UdonSharp/Examples/Utilities/PlayerModSetter.cs) 中。

### 交互
```cs
using UnityEngine;
using UdonSharp;

public class ClickMe: UdonSharpBehaviour
{
    public override void Interact()
    {
        gameObject.SetActive(false);
    }
}
```

### 传送玩家
```cs
using UdonSharp;
using UnityEngine;
using VRC.SDKBase;

public class TeleportPlayer : UdonSharpBehaviour
{
    [SerializeField] Transform targetPosition;

    public override void Interact()
    {
        Networking.LocalPlayer.TeleportTo(targetPosition.position, 
                                          targetPosition.rotation, 
                                          VRC_SceneDescriptor.SpawnOrientation.Default, 
                                          false);
    }
}
```

### 获取玩家
演示如何获取实例中的所有玩家。
```cs
using UdonSharp;
using UnityEngine;
using VRC.SDKBase;

public class GetPlayersExample : UdonSharpBehaviour
{
    // 世界的玩家上限是 10, 所以我们创建一个上限为 20 数组
    VRCPlayerApi[] players = new VRCPlayerApi[20];

    void Start()
    {
        VRCPlayerApi.GetPlayers(players);

        foreach(VRCPlayerApi player in players) {
            if(player == null) continue;
            Debug.Log(player.displayName);
        }
    }
}
```

### UdonSharp 示例脚本
这是一个 UdonSharp 的示例类，演示它如何与其他 UdonSharp Behaviour 进行通信。
```cs
using UdonSharp;
using UnityEngine;
using VRC.SDKBase;
using VRC.Udon.Common.Interfaces;

namespace UdonSharpExample
{
    public class Example : UdonSharpBehaviour
    {
        // UdonSharpBehaviour 类 (影响 Inspector)
        [SerializeField] AnotherExample anotherExample;

        void Start()
        {
            // 等同于 anotherExample.GetProgramVariable("publicBoolean");
            if(anotherExample.publicBoolean)
            {
                // 等同于 anotherExample.SendCustomEvent("RunMethod");
                anotherExample.RunMethod();
            }
        }

        // VRChat 事件
        public override void Interact()
        {
            // 等同于 SendCustomEvent("DoStuff");
            DoStuff();
        }

        public void DoStuff()
        {
            // 这将发送给所有客户端，并在每个客户端上本地运行（包括发送者）
            SendCustomNetworkEvent(NetworkEventTarget.All, "NetworkEventStuff");
        }

        public void NetworkEventStuff()
        {
            // 等同于 anotherExample.SetProgramVariable("publicBoolean", false);
            anotherExample.publicBoolean = false;

            // 等同于 anotherExample.SendCustomEvent("RunMethod");
            anotherExample.RunMethod();

            anotherExample.SendCustomNetworkEvent(NetworkEventTarget.Owner, "DoOwnerStuff");
        }
    }
}
```