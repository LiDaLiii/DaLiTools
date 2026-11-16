# 发版说明

这个仓库只放「能发的东西」：发布包、更新清单、给用户看的说明。源码不在这里。

## 发版前

1. 在源码仓（私有）里把版本号改两处，必须一致：
   - `src-tauri/Cargo.toml` 的 `version`
   - `src-tauri/tauri.conf.json` 的 `version`
2. 编译 release 包（`build.bat release`），得到 `DaLi.exe` + `WebView2Loader.dll`。
3. 打包安装版：`DaLiTools_x.y.z_x64-setup.exe`（必须），以及它的 `.sig` 签名文件。
   便携版（`DaLiTools_x.y.z_x64-portable.zip`）是可选的，**不参与自动更新**：它是解压即用的绿色包，升级方式就是重新下载解压，程序里的「检查更新」不会替换它。
4. 在本仓 `CHANGELOG.md` 顶部加这一版的用户可见变化（只写用户能感觉到什么，不写实现）。
5. 若本轮有公开内容变化（README、许可、文档），一并提交到本仓 `main`。

## 打 Release

1. 在本仓打 tag：`vX.Y.Z`（例如 `v0.3.0`），推送 tag。
2. 在 GitHub 上基于该 tag 新建 Release，标题写成 `DaLiTools x.y.z`，正文从 `CHANGELOG.md` 对应小节粘贴。
3. 上传附件，**三件套必须齐全**，少一样「检查更新」就会失败：
   - `DaLiTools_x.y.z_x64-setup.exe`（安装包）
   - `DaLiTools_x.y.z_x64-setup.exe.sig`（它的签名）
   - `latest.json`（更新清单，下面的 `url` 指向本次安装包）
   便携包 zip 只是可选附件；只传 zip、不传上面三样，等于这次更新发不出去。

## latest.json（自动更新清单）

程序按 `latest.json` 里的版本号和签名判断要不要更新，格式：

```json
{
  "version": "0.3.0",
  "notes": "这一版改了什么（一两段话即可）",
  "pub_date": "2026-11-17T00:00:00Z",
  "platforms": {
    "windows-x86_64": {
      "signature": "<安装包签名串>",
      "url": "https://github.com/LiDaLiii/DaLiTools/releases/download/v0.3.0/DaLiTools_0.3.0_x64-setup.exe"
    }
  }
}
```

- `url` 必须是能公开下载的直链（Release 附件就写 Release 的下载地址）。
- `signature` 用源码仓里的更新签名私钥生成，和安装包一一对应；对不上程序会拒绝安装。
- 清单里写的版本要和安装包里的版本一致，不一致也会被拒。

## 发布后

- 确认 `https://github.com/LiDaLiii/DaLiTools/releases/latest/download/latest.json` 能打开。
- 源码仓的更新地址指向这个地址；地址一改，旧版本用户就顺着新地址更新。
- 首次发版验证：装上一版，打开程序等它检查更新，能看到新版本号、能下载安装、装完版本号变了。
