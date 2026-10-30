# CCR Portfolio — handoff

## 最新：访问故障与GitHub Pages（2026-10-30）
用户报告电脑浏览器连接超时。原Sites API显示active/public，HTTP首页及CSS/JS/图片均200，但实际IAB浏览器显示Cloudflare Sorry, you have been blocked。只证明不同访问路径存在差异，尚不能断定用户超时与IAB拦截根因相同；没有更改或绕过平台安全设置。

使用现有公开仓库的gh-pages分支托管dist内容，地址https://zzcvby.github.io/ccr-portfolio/ 。发布树a6fdc00f8965302b28581ede67350deeb200484a由git subtree split --prefix=dist生成，源代码未修改。Pages配置已核对legacy/gh-pages/根目录/HTTPS，发布验收结果见本地项目主交接最新记录。第一次create接口返回409 already enabled，随后读取现有配置复用，未重复创建仓库。

后续网站修改应先推送main，再从dist生成新的静态树并推送gh-pages，检查Pages构建built及首页/资源HTTP成功。GitHub页面以新地址为准，旧Sites保留。公开状态不变。

## 最新：公开分享（2026-10-30，优先于下文历史状态）
用户明确要求“github别私有，网站还要发给别人看”。已将ZzcVBY/ccr-portfolio改为public，GitHub核对isPrivate=false；Sites访问策略改为public，工具返回成功。网站和二维码允许向访客展示，原私有要求已被用户撤销。GitHub Pages未启用，继续使用既有Sites网址。此轮只改访问权限和文档，未改网站源码，无需重新部署。后续维护应保持公开，除非用户再次变更要求。

更新：2026-10-30。GitHub：https://github.com/ZzcVBY/ccr-portfolio ，已验证 isPrivate=true。默认分支main。

## 目标与完成内容
简洁的CCR个人网站，四页点击/键盘翻页，展示空间白模、科普影像与城市地图案例；支持详情弹窗与三种合作意向。用户提供的微信二维码已加入联系页，可点击原图。用户明确要求GitHub不可见，仓库必须保持私有。

## 技术决策与核心文件
纯静态HTML/CSS/JS，无依赖构建和外部字体/CDN。dist/index.html为页面，style.css为响应式样式，app.js为交互。dist/assets/wechat-qr.jpg为原图字节副本；不裁剪、不重绘。二维码卡片取消旋转，避免扫码时额外倾斜。

.openai/hosting.json记录现有Sites ID；凭据不得入库。GitHub远端名github；Sites发布使用官方workflow的临时远端，互不替代。GitHub上传不会自动部署Sites。

## 测试与验证
node --check通过；原二维码及入库图片SHA256一致：FB718621DA9E94E2F61F55E4F8875C240950D93CBE796C4E9676BEEA8569EC3C。联系页AX实际显示查看微信二维码原图链接与新提示。此前1440/390宽度、翻页、三项目详情、Esc、复制开场白均已验证。

二维码版Sites部署succeeded，commit bee36b7dc715678bd05779d4fffaacfb824fd60f。网站：https://ccr-selected-work-2026.yjl012010.chatgpt.site/#contact 。访问策略已读取确认为custom且仅所有者，无外部访客；本轮未改权限。GitHub源码首次推送同一commit成功，私有状态已通过API核对。

本轮浏览器会话重连遇到browser.user unavailable；联系页AX已验证，后续截图检查未完成。不声称已进行真实微信扫码验证。

## 已知问题
尚未由用户确认扫码结果。视频为静帧案例，城市地图为截图，不是网页内视频播放或3D漫游。网站、GitHub均私有，未配置GitHub Pages、独立域名或公开收录。仓库未提供自动测试框架；当前质量门为语法检查和相关页面验证。

## 失败尝试
gh auth status缓存账号名与gh api user不一致，真实账号通过API确定为ZzcVBY，仓库创建和私有状态以API为准。浏览器旧句柄有失效问题，勿重复视为截图成功。Windows打包应优先System32原生tar.exe，避免MSYS tar将盘符识别为远端。

## 下一步
1. 用户用微信核对二维码并审阅页面。
2. 按用户反馈调整作品与个人介绍，运行语法与相关页面检查。
3. 更新文档，推送github远端；若修改线上页面，复用现有Site获取写凭据并走官方workflow发布，凭据仅经stdin。
4. 没有用户明确授权，不把仓库或网站改为公开，不启用GitHub Pages。
