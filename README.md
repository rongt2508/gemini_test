# A Convergent Web Matrix

一个基于 [Three.js](https://threejs.org/) 的 3D 粒子矩阵可视化网页。粒子点与连线构成发光的空间网络,配合辉光后处理与交互波纹,营造「量子数据流」的视觉效果。复刻自 <https://athreedddgraph.netlify.app/>。

## 特性

- **三种粒子形态**,可循环切换:
  1. **Quantum Gyroid Lattice** —— 螺旋曲面网格(红/橙)
  2. **Celestial Trefoil Multiverse** —— 三叶结(金/橙)
  3. **Cosmic Neural Mandala** —— 同心层球(暖色内核 + 冷色蓝/粉外壳)
- **粒子 + 连线网格**:近邻点自动连线,使用 `AdditiveBlending` 叠加发光。
- **UnrealBloom 辉光**:让粒子产生光晕。
- **量子震荡波纹**:点击空白处触发波纹,粒子沿波纹环变亮、放大后平滑恢复。
- **切换颜色**:5 套预设配色(Ember / Cyan / Verdant / Amethyst / Rose),通过色相旋转实现。
- **视角控制**:拖拽旋转、滚轮缩放。

## 交互与按钮

| 按钮 / 操作 | 功能 |
| --- | --- |
| `Next Shape` | 切换到下一种粒子形态 |
| `Color: xxx` | 循环切换配色主题 |
| `Auto Spin: ON/OFF` | 开关自动旋转 |
| `Reset View` | 复位视角 |
| 点击空白处 | 触发量子震荡波纹 |
| 拖拽 / 滚轮 | 旋转 / 缩放视角 |

## 技术栈

- **Three.js** 0.154.0(通过 import map 从 unpkg CDN 加载)
- `OrbitControls` 视角控制
- `EffectComposer` + `RenderPass` + `UnrealBloomPass` 辉光后处理
- 单文件实现:内联 CSS + 一个 `<script type="module">`

> 页面使用 ES Module + import map,需要通过 HTTP 访问(直接 `file://` 打开会因 CORS 失败)。

## 本地运行

需要联网加载 Three.js CDN。

### 方式一:Node 静态服务器(推荐)

```bash
node serve.js
```

然后访问 <http://localhost:8000>。

### 方式二:Python

```bash
python -m http.server 8000
```

### 方式三:任意静态服务器

把仓库目录作为静态站点根目录即可,例如 `npx serve`。

## 目录结构

```
.
├── index.html   # 主页面(单文件,含全部 CSS 与 JS)
├── serve.js     # 简易 Node 静态文件服务器(本地预览用)
└── README.md    # 项目说明
```

## 许可证

本项目仅用于学习与演示。
