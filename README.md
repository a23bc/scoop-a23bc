# scoop-a23bc 🪣

> @a23bc 的个人 Scoop bucket，收录常用/定制 Windows 应用

[![Scoop](https://img.shields.io/badge/Scoop-Bucket-blue?logo=scoop)](https://scoop.sh)
[![GitHub](https://img.shields.io/badge/GitHub-a23bc/scoop--a23bc-181717?logo=github)](https://github.com/a23bc/scoop-a23bc)

---

## 🚀 快速使用

```powershell/windows terminal
# 1️⃣ 添加 bucket
scoop bucket add a23bc https://github.com/a23bc/scoop-a23bc.git

# 2️⃣ 搜索可用应用
scoop search bucket:a23bc

# 3️⃣ 安装应用（示例）
scoop install qwen-studio
scoop install thunder
scoop install hypomux
```

---

## 📦 收录应用列表


| 应用名称 | 描述 | 备注 |
| :--- | :--- | :--- |
| hypomux | 高性能网络加速与复用工具 | [Hypostasis-Cat/HypoMux](https://github.com/Hypostasis-Cat/HypoMux)<br>🔄️自动更新 |
| qobuzdownloaderx | Qobuz 高解析度无损音乐下载器 | [ImAiiR/QobuzDownloaderX](https://github.com/ImAiiR/QobuzDownloaderX)<br>🔄️自动更新 |
| qobuzdownloaderx-mod | Qobuz 音乐下载器 (MOD 增强版) | [DJDoubleD/QobuzDownloaderX-MOD](https://github.com/DJDoubleD/QobuzDownloaderX-MOD)<br>🔄️自动更新 |
| qoder | 基于通义千问的 AI 原生 IDE | [Qoder官网](https://qoder.com/)<br>🔄️自动更新 |
| qwen-studio | Qwen AI 官方桌面客户端 | [Qwen官网](https://qwen.ai/)<br>🔄️自动更新 |
| stelliberty | 现代化跨平台网络代理客户端 | [Kindness-Kismet/stelliberty](https://github.com/Kindness-Kismet/stelliberty)<br>🔄️自动更新 |
| thunder | 多协议高速下载与云存储工具 | [迅雷官网](https://www.xunlei.com/) |
| tubatools | DIY 硬件检测与系统维护工具箱 | [图吧工具箱官网](https://www.tbtool.cn/) |
| workbuddy | 腾讯全场景 AI 办公效率助手 | [WorkBuddy官网](https://www.workbuddy.ai/)<br>🔄️自动更新 |

> ⚠️ 部分应用为第三方/修改版本，请自行评估风险并遵守原软件许可协议。

---

## ⚙️ 自动更新配置

```json
// manifest 示例片段：启用 checkver + autoupdate
{
  "version": "1.2.3",
  "checkver": {
    "github": "https://github.com/owner/repo",
    "regex": "v([\\d.]+)"
  },
  "autoupdate": {
    "architecture": {
      "64bit": {
        "url": "https://example.com/app-$version-x64.zip",
        "hash": "$sha256"
      }
    }
  }
}
```

```yaml
# .github/workflows/auto-update.yml（已配置）
# • 每日 00:00 UTC 自动检查上游版本
# • 检测到新版本时自动更新 manifest 并提交
# • 支持手动触发：Actions → "Run autoupdate"
```

---



## 🛠️ 开发 & 本地测试

```powershell
# 🔹 添加本地 bucket 进行测试
scoop bucket add test-local ./scoop-a23bc

# 🔹 验证 manifest 语法
scoop cat qwen-studio

# 🔹 强制安装测试（跳过缓存）
scoop install qwen-studio --force

# 🔹 创建新 manifest 模板
scoop new bucket/a23bc/myapp
```

```json
// 📄 新应用 manifest 最小模板
{
  "version": "0.1.0",
  "description": "简短描述",
  "homepage": "https://example.com",
  "license": "MIT",
  "architecture": {
    "64bit": {
      "url": "下载链接",
      "hash": "sha256:填写实际哈希"
    }
  },
  "bin": ["主程序.exe"],
  "checkver": "github",
  "autoupdate": {
    "architecture": {
      "64bit": {
        "url": "https://example.com/app-$version.zip"
      }
    }
  }
}
```

---

## ❓ 常见问题

```text
Q: 这些应用安全吗？
A: 所有 manifest 均校验文件哈希，但部分应用为非官方构建，
   请自行评估风险，建议仅用于个人测试环境。

Q: 为什么某些应用无法安装？
A: 可能原因：
   • 下载源临时不可用
   • 应用依赖未满足（查看 manifest 的 depends 字段）
   • 杀毒软件拦截（部分工具类应用可能被误报）

Q: 可以提 PR 吗？
A: 欢迎！请确保：
   • manifest 符合 Scoop 规范
   • 添加 checkver/autoupdate（如上游支持）
   • 在 PR 描述中说明应用用途和来源
```

---

## 📄 关于 License

```text
🔹 Bucket 仓库本身（即 manifest 编写逻辑、workflow 等）：
   建议添加 MIT / Unlicense，方便自己多设备同步或偶尔分享。

🔹 Manifest 中封装的软件：
   每个 .json 的 "license" 字段应填写该软件本身的协议，
   例如："Proprietary", "MIT", "GPL-3.0-only" 等。

✅ 推荐操作（可选）：
   1. 仓库根目录添加 LICENSE 文件（MIT 简洁通用）
   2. 每个 manifest 正确标注所封装软件的 license 字段
```

---

## 🔗 参考链接

- Scoop 官方文档：https://github.com/ScoopInstaller/Scoop/wiki
- App Manifest 结构规范：https://github.com/ScoopInstaller/Scoop/wiki/App-Manifest
- Autoupdate 配置指南：https://github.com/ScoopInstaller/Scoop/wiki/App-Manifest-Autoupdate
- Checkver 工具源码：https://github.com/ScoopInstaller/Scoop/blob/master/bin/checkver.ps1 
- Scoop 概念说明：https://scoop.netlify.app/concepts/


---

> 💡 本 bucket 为个人维护，不保证长期可用性。  
> 🐛 遇到问题？欢迎提 Issue 或 PR～  
> 🔄 最后更新：2026-8-2
