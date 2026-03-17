# AutoGrid Studio

AutoGrid Studio 是一个基于 JavaFX 的桌面排版工具，用来快速制作多图拼版、科研配图、标签标注和对象注释，并导出为常见图片或 PDF 格式。

当前版本：`1.2.1`

## 项目简介

这个项目面向需要整理多张图片并统一排版、加标签、加标注对象的场景。它支持将多张素材导入到一个网格布局中，再对每个子图设置缩放、标签样式和附加对象，最后导出为适合演示、论文或归档的文件。

项目使用 Java 17 与 JavaFX 17 构建，适合在 macOS 环境中打包为原生应用安装包。

## 主要功能

- 导入图片与 PDF 素材
- 自动生成多图网格布局
- 调整行列数、间距和边距
- 为每个子图单独设置缩放比例
- 创建标签组并批量同步标签位置、样式和文字规则
- 支持自动序列标签与自定义文本标签
- 添加对象标注，包括矩形、椭圆、圆、直线、箭头和文本框
- 区分全局对象与子图对象
- 导出为 `PNG`、`JPG`、`TIFF`、`PDF`
- 保存和打开工程文件，工程扩展名为 `.ags`
- 支持撤销、重做以及工程元数据管理
- 支持中英文界面

## 界面结构

- 左侧：素材、标签、对象管理区
- 中间：主画布与可视化排版区域
- 右侧：属性检查器，用于编辑工程、布局、标签、子图和对象属性
- 顶部：文件、导入、导出、布局、撤销/重做等工具入口
- 底部：缩放、当前选择、工程状态和语言状态提示

## 支持的素材与输出

### 输入

- 常见图片文件
- PDF 文件

### 输出

- PNG
- JPG
- TIFF
- PDF

## 工程文件说明

AutoGrid Studio 使用 `.ags` 作为工程文件扩展名。

保存工程时，程序会：

- 生成一个 `.ags` 工程文件
- 在工程目录下创建 `assets/` 目录
- 将工程引用到的素材复制到工程目录中，方便后续迁移和分享

这意味着把整个工程目录一起复制给别人时，通常可以完整保留素材引用。

## 技术栈

- Java 17
- JavaFX 17
- Gradle
- Jackson Databind
- Apache PDFBox

## 运行环境

建议环境：

- macOS
- JDK 17

如果用于开发或重新打包，请确保命令行可以访问以下工具：

- `java`
- `gradle` 或项目自带的 `./gradlew`
- `jpackage`

## 本地开发运行

在项目 `app` 目录中执行：

```bash
./gradlew run
```

如果只想编译：

```bash
./gradlew build
```

## macOS 打包

项目已经内置了 macOS 原生打包任务，可直接生成 `.app` 和 `.dmg`。

在项目 `app` 目录中执行：

```bash
./gradlew packageInstaller
```

打包成功后，默认输出目录为：

```text
app/build/package/
```

典型产物包括：

- `AutoGrid Studio.app`
- `AutoGrid Studio-1.2.1.dmg`

## 当前已生成的安装包

如果你正在使用当前这份工作目录，现成的 macOS 安装包通常位于：

```text
/Users/geo/java_code/autogridstudio-original/autogridstudio-mac-1.2.1/app/build/package/AutoGrid Studio-1.2.1.dmg
```

## 安装说明

1. 下载 `.dmg` 文件
2. 双击打开安装包
3. 将 `AutoGrid Studio.app` 拖入 `Applications`
4. 首次打开时，如 macOS 出现安全提示，可在“系统设置 > 隐私与安全性”中允许打开

说明：如果安装包未做 Apple Developer ID 签名与公证，部分 macOS 设备可能会显示安全提醒。

## 使用流程建议

1. 新建工程
2. 导入图片或 PDF 素材
3. 调整网格行列、间距和边距
4. 按需要调整子图顺序与缩放
5. 新建标签组并设置标签内容、位置和样式
6. 添加矩形、箭头、文本框等对象标注
7. 保存为 `.ags` 工程
8. 导出为 PNG、JPG、TIFF 或 PDF

## 目录说明

项目核心目录大致如下：

```text
app/
├── src/main/java/        Java 源码
├── src/main/resources/   样式与国际化资源
├── build.gradle.kts      Gradle 构建脚本
├── gradlew               Gradle Wrapper
└── build/package/        原生应用与安装包输出目录
```

## 适用场景

- 科研论文配图
- 多图结果拼版
- 实验流程图或结果图整理
- 带标签和标注对象的图像导出
- 需要保存编辑状态并反复修改的图像排版工作

## 备注

- 项目主程序入口为 `com.autogrid.AppLauncher`
- 应用支持直接打开 `.ags` 工程文件
- 界面内置中文和英文语言资源

如果后续需要对外发布，推荐将 `.dmg` 上传到 GitHub Releases，而不是直接提交到 Git 仓库。
