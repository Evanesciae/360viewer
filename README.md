# 360 Viewer

一个纯前端的 360° 全景查看器，支持 360 全景图与 360 视频播放，采用 iOS 风格的毛玻璃界面。
单文件部署，开箱即用，适合托管在 GitHub Pages 等静态站点。

🌐 **在线演示：<https://360.wzt.hk>**

## ✨ 功能特性

- **360 全景图** —— 等距长方投影（equirectangular）全景图查看
- **360 视频** —— 大文件流式播放，自定义毛玻璃控制条（播放 / 进度 / 时间 / 静音）
- **拖动观看** —— 鼠标 / 触摸拖动环顾四周，双指捏合缩放
- **本地相册** —— 已打开的图片自动归档，按日期分组（今天 / 昨天 / 年月日），苹果相册风格
- **沉浸全屏** —— 全屏 API + iOS 原生视频全屏，带独立退出按钮
- **自动旋转 / 重置视角 / 缩放** —— 一键巡游与复位
- **iOS 风格 UI** —— `backdrop-filter` 毛玻璃、SF 字体、刘海安全区适配
- **零后端、零上传** —— 文件仅在本机内存中处理，刷新即清除，隐私安全

## 🎮 操作方式

| 操作 | 效果 |
| --- | --- |
| 拖动（鼠标 / 手指） | 环顾四周 |
| 双指捏合 | 缩放视场（FOV） |
| 滚轮（桌面） | 缩放 |
| 拖放文件到页面 | 直接打开（图片或视频） |
| `自动旋转` | 画面缓慢自动巡游 |
| `重置视角` | 回到初始朝向与默认缩放 |
| `全屏` | 进入 / 退出全屏 |

## 🛠 技术栈

- [three.js](https://threejs.org/)（ESM + importmap，CDN 加载）—— WebGL 反向球体渲染
- 原生 Web API：`File` / `URL.createObjectURL` / `VideoTexture` / `Fullscreen API`
- 纯 HTML + CSS + JS，无构建步骤、无依赖安装

## 🚀 本地运行

无需安装任何依赖，任选其一：

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

浏览器打开 <http://localhost:8000> 即可。

> ⚠️ 请通过本地服务器访问，直接以 `file://` 打开可能导致部分浏览器限制无法加载。

## 📦 部署到 GitHub Pages

1. Fork 或推送本仓库到 GitHub
2. 仓库 `Settings` → `Pages` → `Source` 选择 `main` 分支
3. 等待构建完成，即可通过 `https://<用户名>.github.io/<仓库名>/` 访问
4. （可选）在仓库根目录添加 `CNAME` 绑定自定义域名

## 📁 项目结构

```
360viewer/
├── index.html            # 全部应用代码（HTML + CSS + JS 单文件）
├── splash.jpg            # 横屏开屏背景图
├── splash-portrait.jpg   # 竖屏开屏背景图（手机）
├── CNAME                 # 自定义域名配置
└── README.md
```

## 🌐 浏览器兼容性

- 桌面：Chrome / Edge / Firefox / Safari（最新版）
- 移动：iOS Safari 15+、Android Chrome
- iOS Safari 的全屏 API 仅对 `<video>` 元素生效，图片模式下「全屏」会隐藏应用 UI；
  若需真正的全屏沉浸，可使用 Safari「添加到主屏幕」以 PWA 方式启动。

## 📝 说明

- 180° 全景视频的渲染接口已预留，后续可扩展。
- 所有文件处理均在浏览器本地完成，不会上传到任何服务器。

## 📄 许可证

[MIT License](./LICENSE)
