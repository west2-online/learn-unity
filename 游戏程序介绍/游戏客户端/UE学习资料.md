# UE 学习资料

> 本资料面向刚接触游戏开发的同学，主要介绍 UE 开发中的基础概念、常用功能以及常见问题。
>
> 本资料基于 Unreal Engine 5.4 编写。

## 前言

本资料面向刚接触游戏开发的同学，主要介绍 UE 开发中的基础概念、常用功能以及常见问题。资料以快速了解和查阅为目的，不作为完整 UE 教程。只看文档不够直观，推荐大家对UE有一个整体了解之后，跟着一个教程，完整做出一个属于自己的游戏，这会对你理解与上手UE非常有帮助。（相信大家作为大学生，在网上找教程自学的能力肯定是有的）

UE编辑器支持使用蓝图和C++制作项目，本资料暂时只介绍蓝图相关内容；UE C++需要有一定编程基础的同学学习，且与传统C++有一点差异。大型UE项目一般都是采用蓝图与C++混合的方式制作，但只使用蓝图系统也完全可以制作出一款属于自己的游戏，所以大家无需担心。

本资料基于Unreal Engine 5.4编写，但使用其他版本的同学也可以进行参考，整体上大同小异，遇到具体问题可以查阅UE官方网站资料 https://dev.epicgames.com/documentation/unreal-engine 。

另外，推荐大家UE编辑器内置语言设为英文，锻炼大家英语文本阅读能力的同时，也能接触到UE最原始的模样，不被奇怪的翻译误导o.O，有些词汇确实不好翻译成中文。

# 一、UE 基础

## 1.1 Unreal Engine 是什么

Unreal Engine（UE）是一款由 Epic Games 开发的游戏引擎，可以用于制作游戏、影视、虚拟现实等内容。

在游戏开发中，UE 可以帮助我们完成：

- 场景制作

- 角色控制

- 动画

- UI

- AI

- 音频

- 特效

- 材质

- 游戏逻辑

- 游戏打包

## 1.2 UE 项目的基本结构

一个 UE 项目通常包含（在项目文件夹下都可见）：

- Content：项目主要资源

- Config：项目配置

- Plugins：插件

- Source：C++ 项目代码（如果使用 C++）

- Saved：运行过程中生成的文件

- Intermediate：编译过程中产生的临时文件

日常开发中最常接触的是 Content。

## 1.3 常见编辑器窗口

- Viewport：用于查看和编辑当前场景，可以查看场景、移动/旋转/缩放 `Actor`、放置游戏对象。

- World Outliner：显示当前 `Level` 中的 `Actor`，可以查找、选择和管理场景中的对象。

- Details：显示当前选中对象的详细属性，例如 `Transform`、`Mesh`、`Collision`、`Material` 等。

- Content Browser：用于管理项目资源，例如 `Blueprint、Material`、`Texture`、`Animation、Sound`、`Level`。

## 1.4 Level、World、Actor、Component

- World：可以理解为游戏运行的世界。

- Level：组成游戏世界的场景，可以理解为游戏中的一张地图或一个场景。

- Actor：可以放入 Level 中的游戏对象，例如玩家、敌人、NPC、门、道具和灯光。

- Component：Actor 的组成部分，用于为 Actor 提供具体功能。一个 Actor 可以拥有多个 Component。

# 二、Blueprint 蓝图基础

## 2.1 Blueprint 是什么

Blueprint（蓝图）是 UE 提供的可视化编程系统。通过蓝图，可以在不编写 C++ 代码的情况下实现大量游戏逻辑。

## 2.2 常用节点

- Event：用于触发一段逻辑，例如 `Event BeginPlay`。

- Variable：用于保存数据，例如 `Health`、`Level`、`IsDead`。

- Branch：相当于程序中的 if，根据条件执行不同逻辑。

- Function：将一段具有独立功能的逻辑封装起来，便于重复使用。

- Custom Event：用于创建自定义事件。

- Sequence：按顺序执行多个执行引脚。

- Loop：用于重复执行一段逻辑。

## 2.3 Cast

`Cast` 用于判断一个对象是否属于指定类型，并在成功后访问该类型的内容。

例如：Other Actor → Cast To BP_Player → 获取玩家属性。

不要为了访问变量就到处 Cast。如果多个不同类型的对象都需要执行相同功能，可以考虑使用 `Blueprint Interface`。

## 2.4 Blueprint Interface

`Blueprint Interface`（蓝图接口）可以让不同类型的对象拥有统一的功能调用方式。

例如玩家、敌人、NPC、宝箱都可以实现 Interact。这样交互系统就不需要分别判断每种对象的类型。

## 2.5 Event Dispatcher

`Event Dispatcher` 可以理解为一种“事件通知”。

例如 Boss 死亡时，可以通知 UI、BGM、任务系统和门等多个系统执行对应逻辑。

# 三、常用数据类型

## 3.1 常见类型

- Bool：真假状态，例如 `IsDead`。

- Integer：整数，例如 `Level`。

- Float：浮点数，例如 `Speed`。

- String / Text：文本。

- Enum：有限的几种状态，例如武器类型、角色状态。

- Struct：将多个相关数据组合在一起，例如玩家属性。

- Array：保存多个数据，例如背包物品列表。

- Map：通过 `Key` 查找对应 `Value`，例如 ItemID → ItemCount。

- Object Reference：引用一个具体对象。

## 3.2 简单示例

Enum：

枚举类`E_WeaponType`中，可以有 `Sword` / `Bow` / `Staff` / `Shield` 等多种分类，他们都属于`E_WeaponType`的一个类型。

Struct：

结构体`PlayerData`中，可以有 `Level` / `HP` / `MaxHP` / `Stamina` / `MaxStamina` / `Attack` 等多个属性，每个`PlayerData`都包含各自的这些属性。

Map：

可以理解为一个键值对映射，一个键对应一个值，不能存在相同的键

`Potion` → 5

`Arrow` → 30

`Key` → 1

# 四、常用系统简介

## 4.1 Character

`Character` 是 UE 中专门用于制作角色的 `Actor` 类型。`Character` 通常包含 `Capsule Collision`、`Skeletal Mesh`、`Character Movement` 和 `Camera`。

`Character Movement` 是`Character`的一个组件，负责处理角色移动、跳跃、下落等功能。

## 4.2 Animation

常见动画资源包括 `Animation Sequence`、`Animation Blueprint`、`Blend Space` 和 `Montage`。

`Animation Blueprint`：用于控制角色动画状态。

`Blend Space`：根据参数混合多个动画，例如根据速度在 Idle、Walk、Run 之间进行混合。

`Montage`：可以理解为动画的一层包装，适合播放攻击、喝药、受击等需要独立控制的动画。

## 4.3 UI

UE 使用 UMG 制作游戏 UI。常见控件包括 `Text`、`Image`、`Button`、`Progress Bar`、`Canvas Panel`、`Vertical Box`、`Horizontal Box` 和 `Overlay`。

通常通过 `Widget Blueprint` 制作 UI。

## 4.4 AI

UE 常用 AI 系统包括 `AI Controller`、`NavMesh`、`Blackboard`、`Behavior Tree`、`State Tree`和 `AI Perception`。

一个简单的敌人 AI 可以实现：巡逻 → 发现玩家 → 追踪玩家 → 进入攻击范围 → 攻击。

## 4.5 Material

Material 用于控制物体的表面效果。常见输入包括 `Base Color`、`Metallic`、`Roughness`、`Normal`、`Emissive` 和 `Opacity`。

`Material Instance` 可以在不修改原 Material 的情况下调整参数。

## 4.6 Audio

常见音频资源包括 `Sound Wave`、`Sound Cue`、`MetaSound` 和 `Audio Component`。

`Sound 2D` 通常用于不受空间距离影响的声音，例如 BGM。

`3D Sound` 可以根据玩家与声音源之间的距离产生音量变化。

## 4.7 Niagara

`Niagara` 是 UE 中用于制作粒子特效的系统，常用于火焰、烟雾、魔法、爆炸、雨雪和环境粒子等效果。

# 五、常用操作

## 5.1 创建 Blueprint

在 `Content Browser` 中右键 → `Blueprint Class` → 选择父类。常见父类有 `Actor`、`Character`、`Pawn`、`PlayerController` 和 `GameMode`。

## 5.2 创建 UI

常见流程：`Create Widget` → `Add to Viewport`。删除 UI：`Remove From Parent`。

## 5.3 获取玩家角色

常见方法：`Get Player Character`。然后根据需要转换为自己的 `Character` 类型。

## 5.4 播放音效

可以使用 `Play Sound 2D`、`Play Sound at Location`、`Spawn Sound 2D` 和 `Spawn Sound Attached`，根据声音是否需要空间位置来选择。

## 5.5 查看 NavMesh

在场景中放置 `Nav Mesh Bounds Volume`，然后按 P 可以显示导航区域。

# 六、常见问题 FAQ

## 6.1 为什么出现 Accessed None？

大家在运行游戏时可能会有报错

例如：Accessed None trying to read property XXX。

通常表示正在访问一个没有有效对象的变量。

排查：

1. 变量是否成功赋值

2. 获取对象的逻辑是否执行

3. 对象是否已经被 `Destroy`

4. 是否在正确的时机访问

## 6.2 为什么 Cast Failed？

说明尝试转换的对象并不是目标类型。

检查获取到的对象到底是什么，以及是否真的需要 Cast。如果多个对象需要统一功能，可以考虑使用 `Interface`。

## 6.3 为什么 AI 不移动？

常见原因：

没有正确设置 `AI Controller`

`Character` 没有正确使用 `AI Controller`

没有 `NavMesh`

`NavMesh` 范围不正确

目标位置无法到达

`Behavior Tree` 没有执行

Move To 失败

## 6.4 NavMesh 是绿色的，但敌人还是不移动

绿色只代表该区域存在可导航区域，还需要检查 `AI Controller`、`Behavior Tree`、`Move To`、目标是否有效以及 `Character Movement` 是否正常。

## 6.5 为什么 Animation Blueprint 只有 Idle？

常见原因：

`Animation Blueprint` 没有正确设置

`State Machine` 没有切换

状态切换条件不正确

`Speed` 等参数没有正确更新

`Skeletal Mesh` 使用了错误的 `Animation Blueprint`

`Skeleton` 不匹配

建议使用 `Animation Blueprint Debug` 模式检查当前状态。

## 6.6 为什么 Montage 不播放？

检查：

1. `Montage` 是否使用正确的 `Skeleton`

2. `Slot` 是否正确

3. `Anim Graph` 中是否存在对应 `Slot`

4. `Montage` 是否真的被调用

5. 播放对象是否正确

## 6.7 为什么 Widget 不显示？

检查 `Create Widget` 的返回值是否有效，以及是否执行了 `Add to Viewport`。

如果仍然没有显示，再检查 `Widget Visibility`、`ZOrder`、`Canvas/Layout`，以及是否被其他 UI 遮挡。

## 6.8 为什么材质颜色和原来的不一样？

可能原因：

`Texture` 本身不是最终颜色

使用了多个 `Texture`

`Base Color` 接线错误

`Color Space / sRGB` 设置问题

`Material` 中存在额外颜色计算

`Lighting` 导致视觉上的颜色差异

如果原材质正常，建议先查看原 `Material` 的节点连接方式。

## 6.9 为什么声音没有播放？

检查：

`Sound Wave` 是否有效

`Sound Cue` 是否有效

播放节点是否执行

`Audio Component` 是否有效

音量是否为 0

是否被 `Sound Concurrency` 限制

3D 声音是否距离太远

## 6.10 为什么编辑器里正常，打包后却报错？

常见原因：

资源没有被正确引用

Cook 时资源没有被包含

路径错误

缺少插件

SDK / 编译环境问题

项目中存在编辑器专用资源

首先查看 `Output Log` / `Packaging Log`，找到最早出现的 Error，再根据错误信息排查。

## 6.11 为什么编辑器报错崩溃？

可能的原因有很多，优先查看报错日志报告，不清楚原因可以问AI，有时候一些很奇怪的原因也会导致崩溃，例如使用中文输入法、重命名资产时把名字删完等。。。

# 七、项目规范

命名并没有强制的要求，但是合理规范的命名可以使你的项目井井有条，更好管理；同时其他人接手你的项目时也不用费尽心思去猜，能有效提高工作效率。

## 7.1 常见资源命名前缀

BP_：Blueprint

WBP_：Widget Blueprint

ABP_：Animation Blueprint

M_：Material

MI_：Material Instance

T_：Texture

S_：Sound

NS_：Niagara System

DA_：Data Asset

DT_：Data Table

例如：BP_Player、WBP_HUD、ABP_Player、M_Player、T_Player_Base。

## 7.2 文件夹

不要将所有资源直接放在 Content 根目录。

示例：

Content

├── Characters

├── Animation

├── UI

├── Audio

├── Materials

├── Textures

├── VFX

├── Maps

└── Systems

具体结构以项目组现有规范为准。

## 7.3 基本协作规范

修改别人制作的内容前先沟通

不随意删除资源

不随意修改公共 Blueprint

提交项目时注意资源依赖

遇到问题先查看报错信息

# 八、学习建议

## 8.1 推荐学习顺序

UE 基础（编辑器操作等）

↓

Blueprint

↓

数据类型

↓

Actor / Component

↓

Character

↓

Animation / UI / AI

↓

根据项目需求继续学习

## 8.2 遇到问题怎么办

UE 的内容非常多，不需要一开始全部学会。

遇到问题时，可以先尝试：

1. 查看报错信息

2. 查看 Output Log

3. 使用 Print String

4. 使用 Blueprint Debugger

5. 检查变量是否为空

6. 检查节点是否执行

7. 搜索对应问题

8. 再向其他成员寻求帮助

能够独立定位问题，比记住大量 UE 节点更加重要。

最后祝大家都能成为优秀的游戏创作者！
