# 如何生成 Android APK 安装包

由于你正在使用 Windows 系统，直接运行 Linux 命令（如 `sudo`, `apt`）会报错。打包 Android APK 需要 Linux 环境。

最简单、无需在电脑上安装 Linux 的方法是使用 **Google Colab**（免费云端服务器）来打包。

## 步骤 1：准备项目文件
1. 确保你的项目文件夹里包含以下文件：
   - `main.py` (及 `src/` 目录)
   - `buildozer.spec`
   - `assets/` (如果有)
2. 将整个项目文件夹压缩成一个 ZIP 包，命名为 `SoulGuardian.zip`。

## 步骤 2：使用 Google Colab 打包
1. 打开 [Google Colab](https://colab.research.google.com/)。
2. 点击 "新建笔记本" (New Notebook)。
3. 在左侧文件栏，点击“上传”按钮，将你的 `SoulGuardian.zip` 上传上去。
4. 在代码单元格中，复制并粘贴以下代码，然后点击运行（播放按钮）：

```python
# 1. 解压项目
!unzip -q SoulGuardian.zip -d project
%cd project

# 2. 安装依赖 (Buildozer 和系统库)
!sudo apt-get update
!sudo apt-get install -y libffi-dev libssl-dev python3-pip
!pip install buildozer cython==0.29.33

# 3. 安装 Android SDK/NDK 并打包 (这一步比较慢，约需 10-15 分钟)
# 注意：第一次运行时会要求同意许可，输入 y 并回车即可
!buildozer android debug
```

## 步骤 3：下载 APK
1. 等待打包完成（最后会显示 `Android packaging done!`）。
2. 在左侧文件栏中，打开 `project/bin/` 文件夹。
3. 你会看到一个 `.apk` 文件（例如 `SoulGuardian-0.1-debug.apk`）。
4. 右键点击该文件，选择 **下载**。
5. 发送到手机安装即可玩！

---

## 常见问题
*   **黑屏/闪退**：通常是因为缺少资源文件或依赖。请检查 `buildozer.spec` 中的 `source.include_exts` 是否包含了所有需要的文件类型（如 png, jpg, ttf, ogg 等）。
*   **触屏没反应**：确保代码中 `src/ui_touch.py` 的逻辑已经生效（我们在游戏中已经开启了 `self.touch_active = True`）。
