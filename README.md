# Ollama Android ARM64 Builder

自动构建 Ollama Android ARM64 二进制文件的 GitHub Actions 工作流。

## 功能

- 🚀 自动从 Ollama 官方仓库编译 Android ARM64 版本
- 📦 支持指定版本构建
- 🔧 使用 Android NDK r26c 交叉编译
- 💾 生成可直接用于 Android 项目的二进制文件

## 使用方法

### 方式 1: 手动触发构建

1. 进入 GitHub 仓库的 **Actions** 页面
2. 选择 **"Build Ollama Android ARM64"** 工作流
3. 点击 **"Run workflow"**
4. 输入要构建的版本（如 `v0.18.3`）
5. 点击 **"Run workflow"**

### 方式 2: 自动触发

推送到 `main` 或 `master` 分支会自动触发构建。

## 构建输出

构建完成后，你可以在以下位置获取文件：

- **Artifacts**: Actions 运行页面的 Artifacts 部分
- **Releases**: 当手动触发时，会自动创建 Release

输出文件结构：
```
release/
└── arm64-v8a/
    ├── ollama          # Android ARM64 可执行文件
    └── version.txt     # 版本号
```

## 在 OllamaServer 项目中使用

1. 下载构建好的 tarball
2. 解压到项目目录：
   ```bash
   tar -xzf ollama-android-arm64-v0.18.3.tar.gz
   cp -r arm64-v8a/* /path/to/OllamaServer/android/app/src/main/assets/arm64-v8a/
   ```
3. 重新构建 APK

## 构建配置

| 参数 | 值 |
|------|-----|
| 目标架构 | arm64-v8a |
| Android API | 33 |
| NDK 版本 | r26c |
| Go 版本 | 1.22 |
| 编译优化 | -O3, LTO |

## 许可证

与 Ollama 原项目相同，遵循 MIT 许可证。
