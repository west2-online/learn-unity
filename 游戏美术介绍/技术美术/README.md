# 技术美术（TA）介绍

技术美术（Technical Artist）是程序和美术之间的桥梁：既要懂美术的审美和流程，又要懂程序的技术和实现，把两者翻译成彼此能听懂的话。

TA 的核心能力是「把效果落地」：美术想要一个风格化渲染 → TA 写 Shader 实现；程序需要素材规范 → TA 定标准和工具链；游戏跑不动 → TA 做性能优化。

> ⚠️ **前置警告**：TA 是国内游戏行业最卷的方向之一，要学的东西很多（Shader、渲染管线、图形学基础、至少一门编程语言、美术工具链）。**没学线性代数的话，学 TA 几乎不太可能**——如果还没学，建议先自学（B 站 3Blue1Brown《线性代数的本质》），或者先按 3D 美术 + 程序两条线培养，等线代基础有了再转 TA。
>
> 如果觉得太多太累，趁早换方向；如果决定走这条路，那就做好长期作战的准备。

## 子路径导航

TA 内部不是铁板一块，报名时先选大方向，后续考核中自然分化：

- **渲染 TA**：Shader、风格化渲染、光照——最经典也最卷的 TA 路线
- **特效 TA**：VFX、粒子（Unity VFX Graph / UE Niagara）、技能与环境特效
- **工具 TA**：DCC 插件、引擎编辑器扩展、自动化管线——「程序里的美术服务」
- **性能 TA**：Profiling、Draw Call / 内存 / 材质变体优化——后期项目刚需

前期地基（线代 + Shader + 引擎架构）四条路都要打，子路径决定后期专精方向。

## 学习资源

### 图形学 / 渲染基础（地基）

- **Shader 入门**：[Hi Shader（Unity 官方，人美声甜的 unity 小姐姐，倾情推荐）](https://learn.u3d.cn/tutorial/hi-shader)
  - 入门走节点化编辑器快速建立感觉（Unity Shader Graph / UE Material Editor 都是连连看），**但连连看只是起步，一两周就该丢掉**
  - 手写 Shader 推荐 B 站「庄懂」入门课 + 冯乐乐《Shader 入门精要》（UE 对应 HLSL 写的 .usf/.ush，原理通用）
- **图形学进阶**：[Games101（建议把闫令琪老师的课程都看完）](https://www.bilibili.com/video/BV1X7411F744/)
- **线性代数**（没学的必补）：[3Blue1Brown《线性代数的本质》](https://www.bilibili.com/video/BV1ys411472E)

### 引擎渲染架构

至少熟悉一个引擎的渲染管线：Unity（SRP/URP/HDRP）或 UE（Forward/Deferred、Nanite、Lumen）、材质、光照、后处理。双引擎都懂是加分项。

### 特效 / 工具 / 性能

- 特效：Unity VFX Graph / Shuriken，UE Niagara，配合自定义材质/Shader
- 工具：Unity 编辑器扩展 / UE Editor Utility Widget / Python 脚本（批量处理素材、自动命名/导入规范检查）
- 性能：Unreal Insights / Unity Profiler，Draw Call、内存、材质变体分析

> 💡 关于 AI：AI 写 Shader 很强，但**你必须理解它写的每一行**。只会复制粘贴的「TA」和会连连看没什么区别，考核时我们会提问的。

## 考核流程

2026 年度 TA 考核大纲见 [`考核流程/美术方向/`](../../考核流程/美术方向/README.md)。
