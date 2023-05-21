# 给席斓的一些练习

## 以下哪个BepInEx插件能够运行？（忽略using）
A.
```csharp
namespace MyPlugin
{
   class Main
   {
      public override void Load()
      {
         Log.LogInfo("Hello!");
      }
   }
}
```
B.
```csharp
namespace TownOfShaBi
{
   class woshishabi:BassPlugin
   {
     static void Main()
     {
        Log.LogInfo("我是傻逼");
     }
   }
}
```
C.
```csharp
class NiHao:BasePlugin
{
  public override void Load()
  {
     Log.LogInfo("hi");
  }
}
```
D.
```csharp
class test
{
   static void Main()
   {
      Log.LogInfo("OK");
   }
}
```

## 下面哪个选项的代码不能够正常修补？
游戏代码：
```csharp
class Game
{
   public bool GameStart(int a)
   {
      //假设前面一堆代码
      return true;
   }
}
```

A:我想要修改返回值
```csharp
[HarmonyPatch(typeof(Game),"GameStart")]
class GameStartPatch
{
   public static void Prefix(bool __result)
   {
      __result=false;
   }
}
```

B:我要取得GameStart的参数a
```csharp
[HarmonyPatch(typeof(Game),nameof(Game.GameStart))]
class Patch
{
   static void Postfix(int a)
   {
      int arg=a;
      //对参数进行处理的代码省略
   }
}
```

C:我不想让它执行GameStart函数了，我想让他执行我的函数
```csharp
[HarmonyPatch(typeof(Game),"GameStart"]
class MyMethod
{
   private static bool Postfix([HarmonyArgument(0)] int a,ref bool __result)
   {
      __result=GameStartPatchMethod(a,__result);
   }
   static void GameStartPatchMethod(int myArg,bool myResult)
   {
      //假设前面写了很多代码
      return !myResult;
   }
}
```

D:我想将GameStart函数的参数a设为int类型的最大值
```csharp
[HarmonyPatch(typeof(Game),nameof(Game.GameStart))]
class MyProgram
{
   public static void Prefix([HarmonyArgument(0)] int a)
   {
      a=Int32.MaxValue;
   }
}


