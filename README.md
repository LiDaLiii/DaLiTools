# DaLiTools

一个「内核 + 模块」的 Windows 桌面工具箱。极简现代风，Windows 10/11。

单个 exe，装上就能用；功能都做成模块，模块是文件夹，放进去就生效，不用重新编译。

<!-- 截图位置：放两张主界面截图（浅色 / 深色），下面这行换成实际图片 -->
> 截图：待补（主界面 · 浅色 / 深色）

## 现在有哪些模块

| 模块 | 做什么 |
| --- | --- |
| 卡片窗 | 把别的程序窗口拖进卡片区，在 DaLiTools 里直接看、直接点、直接打字 |
| 音乐 | 登录自己的 B 站账号搜歌直接听，自带播放器；可从网易云 / QQ 音乐 / 酷狗 / 汽水的歌单链接、长截图或文本导入，逐首到 B 站匹配 |
| 翻译 | 框一块屏幕，把上面的英文就地铺成中文（本地词库，离线，气泡鼠标可穿透） |
| 桌面角色 | 背身干活的小家伙：打字机、待机动作、右键定制 |
| 老板键 | 一键隐藏程序，可改热键 |
| 简洁窗口 | 同一个文件夹不重复开窗 |

## 下载

去 [Releases](https://github.com/LiMengranran/DaLiTools/releases) 下最新版。

- `DaLiTools_x.y.z_x64-setup.exe`：安装版，装完直接双击用。
- 压缩包版：解压到任意文件夹，双击 `DaLi.exe`。

## 系统要求

- Windows 10 / Windows 11（64 位）
- WebView2 Runtime（Windows 11 自带；Windows 10 如果提示缺，装一次 [WebView2](https://developer.microsoft.com/microsoft-edge/webview2/)）
- 不需要装 .NET、Node、Rust 之类的东西

## 怎么加一个模块

模块就是 `modules/` 下的一个文件夹（`manifest.json` + `ui/`）。把别人的模块文件夹整个拷进 `modules/`，重启程序，侧栏就会出现它的图标——不用重新编译，不用装依赖。

自己写模块：复制模板文件夹、改 `manifest.json` 里的 `id` / `name` / `icon`，刷新即可看到。模块接哪几条接口、清单怎么写，见发布仓里的模块开发文档。

## 更新

程序会自己检查更新（设置 → 关于 里也能手动查）。新版从本仓的 Releases 下载，安装包带签名校验，校验不过的不会装。

## 反馈

- 遇到问题、想加功能：开一个 [Issue](https://github.com/LiMengranran/DaLiTools/issues)
- 发版记录见 [CHANGELOG.md](CHANGELOG.md)

## License

[MIT](LICENSE) © 2026 LiMengranran
