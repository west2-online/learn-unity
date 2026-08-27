
# 🚀 UE 学习轮考核

🌟 致各位未来虚幻引擎大师：

欢迎来到 UE 学习轮考核！首先，请允许我们给你一个大大的拥抱——无论你是刚接触虚幻引擎的新人，还是已经写过几行 C++ 的老手，今天你都迈出了非常棒的一步。

虚幻引擎（Unreal Engine，简称 UE） 是全球最顶尖的实时 3D 创作平台之一，从 3A 游戏大作到影视特效、虚拟制片、建筑可视化，甚至元宇宙应用，都离不开它的身影。掌握 UE，就等于掌握了一把打开无限创意世界的钥匙。而 C++ 与蓝图的结合，正是 UE 最核心、最强大的“双引擎”驱动方式。

更重要的是，本次学习轮考核完全允许你使用 AI 辅助！我们鼓励你善用工具，像真正的开发者一样，学会提问、检索和验证。考核的目的不是“卡住你”，而是帮助你梳理知识。所以，请放下心理包袱——考核标准相对宽松，更看重你的思考过程和解决问题的能力。

---

> ⚡ 请从以下两套试卷中【二选一】完成即可：
> - 选 A理论卷：回答第一、二、三大题；
> - 选 B实践卷：完成实践题（包含移动、盖房、门、灯）。

---

## 📄 试卷 A：理论卷

### 一、基础概念题
1. 在UE的C++中，`int`、`float`、`bool`、`FString`分别用来存储什么类型的数据？蓝图中与之对应的变量类型叫什么？

2. 什么是变量？为什么开发中需要使用变量？请分别简述**C++**和**蓝图**中如何声明与初始化变量。

3. 虚幻蓝图中有`LoopFor`（for循环）和`LoopWhile`（while循环），请说明两种循环的区别以及各自适用场景？C++层面`for`与`while`循环区别是否一致？

4. UE C++有哪些条件判断语句？蓝图对应的节点是什么？写出C++基础语法结构，同时写出蓝图节点名称。

5. 什么是函数（Function）？C++函数由哪几部分组成？`void`代表什么含义？蓝图Function和蓝图Macro有什么简单区别？

6. 面向对象三大特性是什么？简述三大特性在UE（C++/蓝图）开发中的体现。

---

### 二、UE C++类与面向对象
> 参考下面ACreature代码，完成1‑6小题
```cpp
#include "Creature.h"

UCLASS()
class TEST_API ACreature : public AActor
{
    GENERATED_BODY()

private:
    FString CreatureName;
    int32 Health;

public:
    UPROPERTY(EditAnywhere)
    int32 HP;

    ACreature();

    UFUNCTION(BlueprintCallable)
    void TakeDamage(int32 DamageValue);
};
```

1. 代码中`CreatureName`、`Health`是什么成员？`HP`加上`UPROPERTY()`对比普通成员变量有什么优势？

2. `ACreature();`是什么？什么时候执行？

3. `TakeDamage`是什么？`UFUNCTION(BlueprintCallable)`宏的作用？

4. `private`、`public`访问修饰符作用，写出UE C++另外两个访问权限。

5. 创建`ABoss`继承自`ACreature`，写出类定义关键代码；什么条件下ABoss可以直接访问父类ACreature成员？

6. 解释`virtual`、`override`、`UCLASS(Blueprintable, BlueprintNativeEvent)`各自作用。

---

### 三、UE Actor生命周期与组件
1. `BeginPlay()`与构造函数（ActorConstructor）执行时机区别，蓝图对应的事件是什么？

2. `Tick()` 和 `FixedTick`（固定时间步Tick）触发频率区别，适用场景？提示：帧率、物理。

3. `GetWorld()->GetDeltaSeconds()`含义，移动逻辑为什么必须乘deltaTime？

4. 组件是UE核心单元。

(1) 补全代码，获取自身身上`UStaticMeshComponent`组件，需要判空保证健壮性。
```cpp
UStaticMeshComponent* MeshComp;
void ACreature::BeginPlay()
{
    
}
```
> 思考：把组件保存为成员变量缓存对比每次GetComponent查找的优劣。

(2) 写出至少3种获取场景其他Actor / Component的方式（C++或蓝图思路）。

---

## 📄 试卷 B：实践卷

> 说明：本套为实操题，请在本地UE5.0+工程完成。C++/蓝图二选一；允许查阅文档、AI辅助；看重逻辑清晰度和最终运行效果。

### 综合实操：移动 + 搭建小屋 + 门 + 灯光
> 需求背景：类似Minecraft，搭建简易白模小屋，实现角色移动、门开关、灯光交互。

|序号|模块|需求描述|
|---|---|---|
|🎮 需求1|角色移动（基础）|使用新版Input Mapping输入系统绑定MoveForward/MoveRight；ACharacter角色水平面XY移动，速度500.f；必须乘DeltaSeconds保证帧率无关；LeftShift按下速度减半；X按键，Output Log打印`TEXT("Boom!")`|
|🏠 需求2|搭建简易小屋|BSP几何体或者StaticMesh白模Cube搭建房子；可以直接拖拽引擎基础物体，也可以C++/蓝图生成|
|🚪 需求3|交互门|墙上放置门物体（Cube代替亦可）；玩家靠近距离小于200，按E，门Yaw旋转90度开门；再次按E转回关闭|
|💡 需求4|灯光交互|屋内放置点光源/聚光灯；按L键切换灯光开关状态（Set Visibility或者Intensity置0复原）|

### ⭐ 附加理论小问（实践卷必做）
沿用ACreature，定义静态成员 `static int32 CreatureCount;`，回答：
1. 静态成员和实例成员区别
2. C++访问静态成员与实例成员语法差异
3. 蓝图能否直接访问C++静态成员？蓝图访问需要增加什么宏？

---

> 🎉 完成任意一套试卷即为通过！放平心态大胆动手。报错是常态,加油！🚀
```
