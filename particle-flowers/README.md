# 粒子花谱 · 手势双生花

两朵由摄像头手势驱动的粒子花，共用一套 WebGL 运行时。

- 入口页：`index.html`（两张卡片分别进入两个版本）
- 花信：`versions/rose/` — 玫瑰，完全张开时外层花瓣散作星场
- 莲境：`versions/lotus/` — 莲花，约八万粒子铺成一池

## 目录结构

```
index.html                 入口页
assets/landing.css         入口页样式
versions/rose/             花信（index.html + src/ + assets/ + creative/）
versions/lotus/            莲境（index.html + src/ + assets/ + creative/）
vendor/three/              three.js r180（ESM）
vendor/gsap/               GSAP 3.15
vendor/mediapipe/          MediaPipe Tasks Vision 1.2.0（vision_bundle.mjs）
```

## 关于运行资源

本仓库只提交源码与文本类依赖，共约 2.4MB。以下资源不进入 Git 历史，运行时从官方 CDN 获取：

| 资源 | 体积 | 来源 |
| --- | --- | --- |
| MediaPipe WASM（6 个文件） | ~41MB | `https://unpkg.com/@mediapipe/tasks-vision@1.2.0/wasm/` |
| 手部关键点模型 `hand_landmarker.task` | 7.5MB | `https://storage.googleapis.com/mediapipe-models/...` |

两处地址在 `versions/*/src/gesture.js` 中集中定义，便于替换为自托管路径。

## 交互

- 允许摄像头后握拳收拢花苞，张开手掌让花瓣层层舒展；完全张开时触发盛开动画。
- 拒绝摄像头或浏览器不支持 WebGL 2 时自动回到手动模式，用滑块控制开合与粒子数量。
- URL 参数 `?still=1` 可冻结动画，便于静态截图。
