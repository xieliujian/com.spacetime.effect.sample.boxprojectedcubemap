# Box Projected Cubemap 示例工程

本仓库是一个 **Unity 示例项目**，用于演示 [com.spacetime.effect](Packages/com.spacetime.effect/) 中的 **盒子投影 Cubemap（Box Projected Cubemap）** 反射：在矩形房间、走廊等方盒型空间中，让反射探针生成的 Cubemap 按包围盒正确投影，从而改善门窗、挂画等物体在墙面上的反射表现。

## 环境要求

| 项 | 版本 |
|----|------|
| Unity Editor | **2022.3.35f1c1**（见 `ProjectSettings/ProjectVersion.txt`） |
| 渲染管线 | **Universal RP (URP)** 14.0.11 |

使用接近的 **Unity 2022.3 LTS** 与 **URP 14.x** 通常即可正常打开工程；若包版本不一致，以 `Packages/manifest.json` 为准。

## 内嵌包

| 包 | 说明 |
|----|------|
| [com.spacetime.core](Packages/com.spacetime.core/) | SpaceTime 基础框架（本示例随工程一并提供） |
| [com.spacetime.effect](Packages/com.spacetime.effect/) | 视觉效果包：盒子投影 Cubemap、Sun Shaft 等（本示例主要使用前者） |

## 快速开始

1. 用上述 Unity 版本打开本仓库根目录（包含 `Assets/`、`ProjectSettings/`、`Packages/` 的文件夹）。
2. 在 **Project** 窗口中打开示例场景：  
   **`Assets/Scenes/BoxProjectedCubemap.unity`**
3. 进入 **Play** 或 **Scene 视图** 查看效果；也可对比默认模板场景 `Assets/Scenes/SampleScene.unity`。

## 使用盒子投影（概要）

1. 在场景中建 **ReflectionProbe**，包裹目标区域并烘焙/更新 Cubemap。
2. 在探针所在物体上挂 **`ReflectionProbeParam`**（随 `com.spacetime.effect` 提供），用于同步包围盒数据。
3. 在编辑器中通过 **GameObject** 菜单执行 **Copy / Paste**（见下方），将探针参数写入需要反射的材质的 Shader 属性（`_UseBoxCubeRefl`、`_BoxCubeReflCenter` 等）。

**详细步骤、参数说明、Shader 原理与注意点** 见包内文档：

- **[盒子投影 Cubemap 使用说明](Packages/com.spacetime.effect/readme/BoxProjectedCubemap/BoxProjectedCubemap.md)**

其他效果（如 Sun Shaft）说明见 [SunShaft.md](Packages/com.spacetime.effect/readme/SunShaft/SunShaft.md)。

## 项目结构（摘录）

```
com.spacetime.effect.sample.boxprojectedcubemap/
├── Assets/Scenes/           # 示例场景（含 BoxProjectedCubemap.unity）
├── Packages/
│   ├── com.spacetime.core/  # 基础包
│   ├── com.spacetime.effect/ # 效果包（Shader、Runtime、Editor 工具）
│   └── manifest.json
└── ProjectSettings/         # Unity 工程设置
```

## 开发与扩展

- 包内效果与脚本的结构说明、命名空间、程序集划分等，可参阅：  
  [Packages/com.spacetime.effect/CLAUDE.md](Packages/com.spacetime.effect/CLAUDE.md)  
  [Packages/com.spacetime.core/CLAUDE.md](Packages/com.spacetime.core/CLAUDE.md)

## 参考

- [Catlike Coding – Rendering Part 8](https://catlikecoding.com/unity/tutorials/rendering/part-8/)（盒子投影相关背景）

---

**说明**：`README` 中指向的部分外链截图位于上游 `com.spacetime.effect` 仓库的 `Doc` 目录；若链接失效，请以包内 `readme/BoxProjectedCubemap/BoxProjectedCubemap.md` 的文字说明为准。
