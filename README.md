# Rime 配置备忘录

## Rime 简介
摘自官方[wiki](https://github.com/rime/home/wiki/RimeWithSchemata#rime-%E6%98%AF%E5%95%A5)：

> Rime 不是一种输入法。是从各种常见键盘输入法中提炼出来的抽象的输入算法框架。

Rime是开源软件，允许任何人在其基础上开发输入法。常见的如下：

|平台| 输入法| 维护者 |
| --- | --- | --- |
|Windows|小狼毫 Weasel| 官方 |
|macOS | 鼠须管 Squirrel |官方 |
|Linux | 中州韵 ibus-rime |官方 |
|Chrome OS | 真文韵 | 第三方（FydeOS团队） |
|Android | 同文 | 第三方 |

通常我们只需要关注前两个。

### 安装方式

#### Windows 
去[项目主页](https://rime.im/download/)下载，然后一路Next完成安装。

#### macOS
去项目主页下载安装，或者使用 `brew`

```bash
brew install --cask squirrel
```
接着注销当前用户或者重启，在系统设置里面启用鼠须管输入法。另外推荐把通知权限打开。



## Rime 特点

### Pros
* 高度可定制。软件不仅自身开放源代码，而且提供了大量可供用户配置的选项。
* 不联网，没有隐私顾虑。

### Cons
* 默认配置不好用，且自己配置上手难度较大。
* 没有网络热词，云联想。

综上所述，Rime适合热衷于折腾或者重视隐私保护的用户。不过我并非是这二者之一，接触到它是由于ChromeOS系统没有自带双拼输入法，然后Windows LTSC 2021下微软拼音输入法有bug无法使用等机缘巧合……

不过，正如ESLint有 `eslint-config-airbnb`, zsh有 `Oh My Zsh` 一样，用Rime也没必要按照手册逐行配置，直接抄社区的答案就好了。

## 安装词库

前面说到，Rime不联网，它是依赖用户在本地安装好的词库来推断要输入的词语。

推荐使用[雾凇拼音](https://github.com/iDvel/rime-ice)，它包含了丰富的中英和Emoji词库和常用的双拼输入法映射表。

可以直接克隆GitHub Repository然后拷贝到用户配置文件夹，

|平台| 输入法| 目录 |
| --- | --- | --- |
|Windows|小狼毫 Weasel| `%APPDATA%\Rime` |
|macOS | 鼠须管 Squirrel |`~/Library/Rime/` |

也可以使用Rime官方维护的配置文件安装脚本`东风破 plum`，配置代理之后，
macOS输入下面代码：

```bash
curl -fsSL https://raw.githubusercontent.com/rime/plum/master/rime-install | bash -s -- iDvel/rime-ice:others/recipes/full
```

Windows在程序安装目录下打开命令提示符，输入下面代码：
```bat
rime-install.bat iDvel/rime-ice:others/recipes/full
```

最后在系统托盘的选项里面点重新部署更新配置文件，将配置应用生效。

## 编辑皮肤

小狼毫和鼠须管的皮肤配置并不兼容。

自己调色的过程很煎熬，推荐从互联网上搜索自己想要皮肤，或者直接用本仓库的仿系统自带输入法皮肤，然后将代码覆盖掉用户配置文件下相应的文件。

|平台| 输入法| 配置文件 |
| --- | --- | --- |
|Windows|小狼毫 Weasel| `weasel.custom.yaml` |
|macOS | 鼠须管 Squirrel |`squirrel.custom.yaml` |

同样是记得点重新部署。

## 选择方案

修改 `default.custom.yaml` 里面的候选词数量，翻页按键等设置。把自己常用的输入方案（全拼或双拼）加入到方案列表里面，保存并重新部署。

敲击Control加数字1左边的反引号键，可以切换简繁中文，全角半角符号等。

至此所有配置就到此结束了。如果要进一步配置，可以阅读官方wiki或者下面的博文

## 其他语言
[日文输入法方案](https://github.com/gkovacs/rime-japanese)

## 参考

[Rime Squirrel 鼠须管输入法配置详解 - 三十年河東(SSNHD.COM)-博客、分享](https://ssnhd.com/2022/01/06/rime/)

[LufsX/rime: Rime（中州韵）全拼与双拼的自用配置方案](https://github.com/LufsX/rime)
