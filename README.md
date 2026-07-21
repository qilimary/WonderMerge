# 万象合成（WonderMerge）

一款原生 Android 合成游戏。把同等级圆形物体放到一起，它们会合成为下一级；物体堆积并持续越过警戒线时游戏结束。

## 已实现功能

- 三套完整主题：水果、水母、星球，每套 11 个等级。
- 两种模式：
  - **随机模式**：当前物体投放后，才揭晓下一枚。
  - **可视模式**：同时显示当前物体和下一枚。
- 两种模式独立计分；并进一步按主题分别保存最高分。
- 自制圆形物理：重力、碰撞、摩擦、弹性、旋转、连锁合成。
- 越线倒计时判负、危险提示、合成粒子、加分浮字、震动和提示音。
- 三套主题全部由 Canvas 程序化绘制，不依赖外部图片素材。
- 竖屏沉浸式界面，支持 Android 6.0 及以上系统。

## GitHub 自动构建 APK

项目已经包含 `.github/workflows/android.yml`。每次上传或修改代码，GitHub Actions 都会自动构建调试版 APK。

### 手机上传步骤

1. 打开 `https://github.com/new`。
2. Repository name 可填写 `WonderMerge`。
3. 选择 Public 或 Private 均可。
4. 不要勾选自动添加 README、`.gitignore` 或 License，然后创建仓库。
5. 在手机上解压本项目 ZIP。
6. 回到仓库，点 **Add file → Upload files**，上传解压后的全部文件和文件夹。
7. 确认 `.github/workflows/android.yml` 也被上传，然后提交。
8. 打开仓库顶部的 **Actions**，进入 **Build Android APK**。
9. 等构建显示绿色对勾后，打开该次运行，在页面底部 **Artifacts** 中下载 `WonderMerge-APK`。
10. 解压下载的构建产物，安装 `WonderMerge-debug.apk`。

### 手机看不到 `.github` 文件夹怎么办

部分安卓文件管理器会隐藏以点开头的文件夹。项目根目录额外放了一份：

`ANDROID_BUILD_WORKFLOW_BACKUP.yml`

此时在 GitHub 仓库中手动创建：

`.github/workflows/android.yml`

再把备份文件内容完整复制进去并提交即可。提交后 Actions 会自动开始构建。

## 手动运行 Actions

进入仓库的 **Actions → Build Android APK → Run workflow**，可以随时重新构建。

## 修改入口

- 游戏界面、菜单和交互：`GameView.java`
- 物理、合成和判负：`GameWorld.java`
- 水果、水母、星球绘制：`OrbRenderer.java`
- 等级名称、颜色、大小和分数：`ThemeData.java`

Java 源码目录：

`app/src/main/java/com/qili/wondermerge/`

## 构建配置

- Android Gradle Plugin：8.13.2
- Gradle：8.13（由 GitHub Actions 自动安装，不需要上传 Gradle Wrapper）
- JDK：17
- compileSdk / targetSdk：36
- minSdk：23

## 素材与许可

项目没有复制其他合成游戏的源码、图像、音乐、角色或商标。游戏代码使用 MIT License；详细说明见 `LICENSE` 和 `THIRD_PARTY_NOTICES.md`。
