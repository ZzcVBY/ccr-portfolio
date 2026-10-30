# CCR Portfolio

CCR 的个人作品集：空间建模、科普影像与城市交互探索。

本仓库为私有仓库。二维码为所有者提供的真实联系图片，请保持私有；不要自行开启 GitHub Pages 或修改仓库可见性。

## 本地预览

无需安装依赖。在仓库目录执行：

```sh
python -m http.server 8792 --directory dist
```

打开 http://127.0.0.1:8792 。也可直接打开 dist/index.html。

## 文件

- dist/index.html：四个页面及项目详情。
- dist/style.css：响应式视觉设计。
- dist/app.js：翻页、弹窗与沟通意向。
- dist/assets/：作品图与所有者微信二维码。
- .openai/hosting.json：已有 Sites 项目标识，不是凭据；不要新建重复 Site。
- PROJECT_STATUS.md：可跨设备继续工作的交接。

## 检查

```sh
node --check dist/app.js
```

真实二维码保持原图，不使用生成或重绘。二维码可点击查看完整大图；手机扫码目标需要所有者用微信确认。
