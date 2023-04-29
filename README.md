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
     Log.LogInfo("sb");
  }
}
```
D.
```csharp
class sb
{
   static void Main()
   {
      Log.LogInfo("OK");
   }
}
```



