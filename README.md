<p align="center"><img src="./assets/icon.png" width="100" height="100"></p>

<p align="center"><strong>TkForge</strong></p>
<p align="center">在 Figma 中拖放，轻松创建 Python 图形用户界面</p>
<p align="center"><a href="https://producthunt.com/products/tkforge">在 Product Hunt 上点赞</a> • <a href="https://patreon.com/axorax">捐赠</a></p>

> [!IMPORTANT]  
> 这只是一个粗略的翻译，可能并不准确。

## 📰 目录

- [为什么？](#-why-and-how)
- [应用程序预览](#-app-preview)
- [特点](#-features)
- [使用指南](#-usage-guide)
- [可用名称](#-available-names)
- [具有独特特征的名字](#-names-that-have-unique-features)
- [CLI 使用指南](#-cli-usage-guide)
- [在 Windows 环境变量中添加 CLI exe](#-add-the-cli-exe-to-the-environment-variables-in-windows)

## ❓ 为什么？

ParthJadhav 已经用 Tkinter Designer 完成了类似的工作，但我喜欢这个概念，并想从头开始做一个类似的东西，甚至做得更好。TkForge 与 Figma API 交互，获取文件的详细信息，并将其转化为代码。首先，它获取文件数据并将其转换为只包含必要细节的格式，然后再将其转换为代码。这个项目花费的时间比我预计的要长很多。

## 💻 应用程序预览

![TkForge 应用程序预览](./assets//preview.png)

## 🔥 特点

- 超级易用
- 拖放式图形用户界面制作工具
- 支持占位符文本
- 支持多个框架
- 根据背景自动将前景设置为黑色或白色（不一定准确）

## ✨ 使用指南

首先，您需要从发布页面下载可执行文件。然后，您需要创建一个 Figma 标记并复制项目的网址。然后，打开应用程序，将令牌和项目的网址粘贴到应用程序中，点击按钮即可启动魔法！🪄

在 Figma 项目中，确保为所有元素添加正确的名称。

## 🧿 可用名称

| 名称                                   | Tkinter 元素      |
| -------------------------------------- | ---------------- |
| `text` (你也可以给它起任何名字)          | canvas text      |
| `button`                               | button           |
| `image`                                | canvas image     |
| `textbox`                              | entry            |
| `textarea`                             | text             |
| `spinbox`                              | spinbox          |
| `rectangle`                            | canvas rectangle |
| `circle`                               | canvas circle    |
| `oval`                                 | canvas oval      |
| `line`                                 | canvas line      |
| `label`                                | label            |
| `scale`                                | scale            |
| `listbox` (使用前请阅读下文)            | listbox          |

如果任何元素以这些名称开头，那么它将被视为该 Tkinter 元素。例如，"矩形 1"、"矩形"、"矩形"、"RecTanGle 69 "都将被视为矩形。大小写并不重要。

## 💎 具有独特特征的名字

### `label`

如果以后想更改文本，可以使用标签代替文本。

### `circle` and `oval`

椭圆形和圆形的作用相同，因此可以任选其一。

### `circle`, `oval`, `rectangle` and `line`

支持描边颜色和描边宽度，这意味着如果您在 Figma 中为它们添加了描边，它们在 Tkinter 设计中也会以相同的描边和描边宽度显示。

### `textarea` and `textbox`

要添加占位符文本，只需在元素名称后加上空格即可。例如，`textbox Hello world` 或 `textarea Hello world`。要设置占位符文本的颜色，可添加 `placeholder_fg="color_here"`。例如

```python
textbox_1 = TkForge_Entry(
    placeholder="Code Example",
    placeholder_fg="#fff"
)
```

使用 `textbox_1.is_placeholder(False)` 来确保插入的文本不会继承占位符的颜色。使用 `textbox_1.get_placeholder()`读取占位符文本。Tkinter 中的占位符文本可能需要在各种情况下进行额外处理。

### `scale`

对于标尺元素的 from、to 和 orient 值，可以将它们一个接一个地放在名称后面，中间用空格隔开。例如，如果我想要一个 from=10、to=50 和 orient=HORIZONTAL 的缩放比例，那么我可以使用 `scale 10 50` 或 `scale 10 50 HORIZONTAL`，如果我想要 orient=VERTICAL 的缩放比例，那么我可以使用 `scale 10 50 VERTICAL`。

### `listbox`

建议避免使用`listbox`，因为它会将高度和宽度扭曲几个像素。Figma 单位无法正常工作，因此我不得不用特定的数字来除以这些单位，以接近 Figma 的外观。

## 🔮 CLI 使用指南

如果要从 Python 文件运行，则使用 `python tkforge.py YOUR_ARGUMENTS_HERE` 。

您可以使用 `tkforge --help` 获取帮助命令。如果您使用的是 Python 文件，请使用 `python tkforge.py --help` 。

如果您没有在环境变量中添加 CLI 可执行文件，则可能需要使用 `./tkforge.exe` 或类似命令。

下面是一些使用示例：

### 基于标志的语法

```
tkforge --id my_id --token my_token --out ./app
```

如果希望在当前目录下输出，可以使用以下任意一条命令：

```
tkforge --id my_id --token my_token --out .
```

```
tkforge --id my_id --token my_token
```

### 位置语法

```
tkforge my_id my_token output_path
```

如果希望在当前目录下输出，可以使用以下任意一条命令：

```
tkforge my_id my_token .
```

```
tkforge my_id my_token
```

## 🪟 在 Windows 环境变量中添加 CLI exe

步骤 1：创建一个任意名称的文件夹，如 "tkforge"。

步骤 2：将 TkForge CLI exe 文件放到该文件夹中

第 3 步：将 exe 文件从 `tkforge-cli.exe` 重命名为 `tkforge.exe` 。

第 4 步：复制路径名。

复制路径名示例： `C:\Users\PC\Downloads\tkforge`

不要复制".exe "的路径，复制文件夹的路径。

如果路径名两边都有引号，如`"C:\Users\PC\Downloads\tkforge cli"`，则确保去掉引号。

第 5 步：打开 "编辑系统环境变量 "应用程序

第 6 步：点击 "环境变量..."，然后在 "系统变量 "中点击 "路径

第 7 步：然后点击 "编辑"，再点击 "新建 "并粘贴路径

第 8 步：点击 "确定"、"确定 "和 "确定"，然后就完成了！

---

<p align="center"><a href="https://www.patreon.com/axorax">在 Patreon 上支持我</a> — <a href="https://github.com/axorax/socials">查看我的社交网站</a></p>
