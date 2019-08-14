# Conda工具使用
[Back home](../README.md)

96  Himryang 
 0.4 2017.03.15 20:59* 字数 6156 阅读 48748评论 7喜欢 50

## 1. 介绍
任何语言的包，依赖和环境管理：Python，R，Ruby，Lua，Scala，Java，Javascript，C / C ++，FORTRAN

Conda是一个开源包管理系统和环境管理系统，用于安装多个版本的软件包及其依赖关系，并在它们之间轻松切换。 它适用于Linux，OS X和Windows，是为Python程序创建的，但可以打包和分发任何软件。

Conda包括在Anaconda和Miniconda。 Conda也包括在Anaconda的Continuum订阅中，它为Python，R，Node.js，Java和其他应用程序堆栈提供现场企业包和环境管理。 Conda在pypi中也是可用的，虽然这种方法可能不是最新的。

Miniconda是一个小的“引导”版本，只包括conda，Python和它们依赖的包。 超过720个科学软件包及其依赖项可以使用“conda install”命令从Continuum存储库单独安装。

Anaconda包括conda，conda-build，Python和超过150个自动安装的科学包及其依赖项。 与Miniconda一样，可以使用“conda install”命令单独安装超过250个额外的科学软件包。

pip install conda使用pypi上发布的版本。 此版本允许您使用任何python安装创建新的conda环境，然后将新版本的Python安装到这些环境中。 这些环境仍被认为是“Anaconda安装”。

conda 命令是管理Anaconda安装的主要接口。 它可以查询和搜索Anaconda软件包索引和当前的Anaconda安装，创建新的conda环境，以及在现有的conda环境中安装和更新软件包。

## 2. 下载
**2.1 用 Anaconda 还是 Miniconda？**
选择Anaconda：

是新到conda或Python
想方便自动安装Python和超过150个科学包
有时间和磁盘空间（几分钟和3 GB）
不想安装要单独使用的每个软件包
Anaconda下载地址：http://continuum.io/downloads
选择Miniconda：

不介意安装要单独使用的每个软件包
没有时间或磁盘空间一次安装超过150个软件包
只是想快速访问Python和conda命令，并希望稍后整理其他程序
Miniconda下载地址：https://conda.io/miniconda.html
**2.2 选择哪个版本的Anaconda或Miniconda？**
无论您使用Anaconda还是Miniconda，请选择最新版本
只有当您为特定目的测试或需要旧版本时，才应从归档中选择旧版本
**2.3 选择GUI安装程序还是命令行安装程序？**
无论您是在Linux，OS X还是Windows，都有一个安装程序，使您更容易。

如果不希望在终端窗口中输入命令，请选择GUI安装程序
如果GUI使您变慢，请选择命令行版本
**2.4 选择什么版本的Python？**
最新版本的Python 2是2.7，包括在Anaconda和Miniconda
Python的最新稳定版本是3.5，包含在Anaconda3和Miniconda3中
您可以通过下载任何版本并创建一个新的环境，只需点击几下，轻松地设置Python的其他版本，如3.4
## 3. 安装
**3.1 快速安装**
Conda是一个跨平台的软件包和环境管理器，可以运行和更新软件包及其依赖关系。它允许您轻松在本地计算机上的环境之间设置和切换。 Conda包括在所有版本的Anaconda和Miniconda。

Miniconda安装要求
32位或64位计算机，400 MB可用，Linux，OS X或Windows。
注意：如果您选择安装完整的Anaconda软件包，则需要3GB的可用磁盘空间。

安装说明
**Windows Miniconda安装**
在浏览器中下载Miniconda Windows安装程序，然后双击.exe文件并按照屏幕上的说明进行操作。如果不确定任何设置，就接受默认值，可以稍​​后更改。
注意：完成后，将打开一个新的终端窗口。如果没有，请单击开始 - 运行 - 命令提示符。
要测试安装，请输入命令conda list。如果已安装正确地，您将看到已安装的软件包列表。
接下来，去30分钟测试看看吧。

**Windows Miniconda更新**
使用开始 - 运行 - 命令提示符打开终端窗口，导航到anaconda文件夹，然后键入conda update conda。

**Windows Miniconda卸载**
转到控制面板，单击“添加或删除程序”，选择“Python 2.7（Miniconda）”，然后单击删除程序。

**OS X Miniconda安装**
在您的浏览器中下载Miniconda OS X安装程序，然后在您的终端窗口键入以下内容，并按照安装程序屏幕上的提示进行操作。如果不确定任何设置，就接受默认值，可以稍​​后更改。

**bash Miniconda3-latest-MacOSX-x86_64.sh**
现在关闭并重新打开终端窗口以使更改生效。要测试安装，请输入命令conda list。如果已安装正确地，您将看到已安装的软件包列表。
接下来，去30分钟测试看看吧。

**OS X Miniconda更新**
打开终端窗口，导航到anaconda目录，然后键入conda update conda。

**OS X Miniconda卸载**
要卸载Miniconda，打开一个终端窗口并删除整个miniconda安装目录：rm -rf ~/miniconda。你也可以编辑~/.bash_profile并删除从你的PATH环境变量中删除miniconda目录，并删除隐藏.condarc文件以及可能已创建的.conda和.continuum目录在主目录下用rm -rf ~/.condarc ~/.conda ~/.continuum。

**Linux Miniconda安装**
在您的浏览器中下载Miniconda安装程序Linux，然后在您的终端窗口键入以下内容，并按照安装程序屏幕上的提示操作。如果不确定任何设置，就接受默认值，可以稍​​后更改。

**bash Miniconda3-latest-Linux-x86_64.sh**
现在关闭并重新打开终端窗口以使更改生效。要测试安装，请输入命令conda list。如果已安装
正确地，您将看到已安装的软件包列表。
接下来，去30分钟测试看看吧。

**Linux Miniconda更新**
在终端窗口中，键入以下命令：conda update conda

**Linux Miniconda卸载**
要卸载Miniconda打开终端窗口并删除整个miniconda安装目录：rm -rf ~/miniconda。你也可以编辑~/.bash_profile并删除从你的PATH环境变量中删除miniconda目录，并删除隐藏.condarc文件以及可能已创建的.conda和.continuum目录在主目录下用rm -rf ~/.condarc ~/.conda ~/.continuum。

**3.2 完整安装**
如果你匆忙，试试我们的两分钟的Miniconda快速安装。
Miniconda只包括conda，conda-build和它们的依赖，所以你可以干净，快速地安装。
以下介绍完整安装Anaconda(其中包括conda，conda-build和150+开源包)。

在Windows，OS X和Linux上，最好为本地用户安装Anaconda，它不需要管理员权限，是最强大的
安装类型。Anaconda也可以安装在系统范围内，这需要管理员权限。
提示：有关使用OS X或Windows的图形安装程序的安装说明，请参阅The Anaconda Install页面。

Miniconda安装要求
32或64位计算机，32MB可用，Linux，OS X或Windows。
300 MB下载Anaconda plus另外300安装它。
注意：如果选择用户可写安装位置，则不需要管理或root权限来安装Anaconda。

**安装说明**
Windows Anaconda安装
在您的浏览器中下载Windows的Anaconda安装程序，然后双击.exe文件，并按照屏幕上的说明进行操作。如果不确定任何设置，只需接受默认值，因为它们都可以稍​​后更改。
注意：完成后，将打开一个新的终端窗口。如果没有，请单击开始 - 运行 - 命令提示符。

* Windows Anaconda更新
使用开始 - 运行 - 命令提示符打开终端窗口，导航到anaconda文件夹，然后键入conda update conda。

* Windows Anaconda卸载
转到控制面板，单击“添加或删除程序”，选择“Python 2.7（Miniconda）”，然后单击删除程序。

* OS X Anaconda安装
在您的浏览器中下载OS X的Anaconda安装程序，然后双击.pkg文件，并按照屏幕上的说明进行操作。如果不确定任何设置，只需接受默认值，因为它们都可以稍​​后更改。
注意：安装将在您关闭并重新打开终端窗口后才生效。

* OS X Anaconda更新
打开终端窗口，导航到anaconda目录，然后键入conda update conda。

* OS X Anaconda卸载
要卸载Anaconda打开终端窗口并删除整个anaconda安装目录：rm -rf ~/anaconda。你也可以编辑~/.bash_profile并删除从你的PATH环境变量中删除anaconda目录，并删除隐藏.condarc文件以及可能已创建的.conda和.continuum目录在主目录下用rm -rf ~/.condarc ~/.conda ~/.continuum。

* Linux Anaconda安装
在您的浏览器中下载Linux的Anaconda安装程序，然后在您的终端窗口中键入以下内容并按照提示进行操作安装程序屏幕。如果不确定任何设置，只需接受默认值为他们都可以改变以后：
```sh
bash Anaconda-latest-Linux-x86_64.sh
```

注意：在您关闭并重新打开终端窗口后，安装才会生效。

* Linux Anaconda更新
在终端窗口中，键入以下命令：conda update conda。

* Linux Anaconda卸载
要卸载Anaconda打开终端窗口并删除整个anaconda安装目录：rm -rf ~/anaconda。你也可以编辑~/.bash_profile并删除从你的PATH环境变量中删除anaconda目录，并删除隐藏.condarc文件以及可能已创建的.conda和.continuum目录在主目录下用rm -rf ~/.condarc ~/.conda ~/.continuum。

## 4. 测试(试驾)
要开始conda30分钟的测试，你应该已经按照我们的2分钟快速安装指南去下载，安装和更新Miniconda，或者已经下载，安装和更新Anaconda或Miniconda 。
注意：安装后，请确保已经关闭，然后重新打开终端窗口，以使更改生效。

**Conda试驾里程碑：**

USING CONDA。首先，我们将验证您已安装Anaconda或Miniconda，并检查它是否已更新到当前版本。 3分钟。
MANAGING ENVIRONMENTS。接下来，我们将通过创建几个环境来玩，您可以学习在环境之间轻松切换。我们还将验证您所处的环境，并准确地复制环境作为备份。 10分钟。
MANAGING PYTHON。然后我们将检查哪些版本的Python可用于安装，安装另一个版本的Python，并在版本之间切换。 4分钟。
MANAGING PACKAGES。我们来玩包。我们将a）列出您的计算机上安装的软件包，b）查看可用软件包列表，以及c）使用conda install安装和删除一些软件包。对于使用conda安装不可用的软件包，我们将d）搜索Anaconda.org。对于不在这两个位置的包，我们将e）与pip包管理器安装一个包。我们还将安装一个30天免费试用Continuum的商业包IOPro。 10分钟。
REMOVING PACKAGES，ENVIRONMENTS，或CONDA。如果你愿意，我们将通过删除一个或多个测试包，环境或conda结束测试。 3分钟。
TOTAL 30分钟

提示：只要您想查看任何命令的完整文档，请键入命令后跟--help。
例如，要了解conda update命令：
```sh
conda update --help
```

**4.1 管理conda**
Conda既是包管理器，也是环境管理器。一个包管理器可以帮助你找到和安装软件包。使用几个命令，您可以设置一个完全独立的环境来运行不同版本的Python，然后继续在您的正常环境中运行您常用的Python版本。这就是像conda这样的环境管理工具的力量。

提示：无论您是使用Linux，OS X还是Windows命令提示符，在终端窗口中输入的conda命令，除非另有说明，否则都是相同的。

* 验证conda已安装
为了确保您在正确的地方开始，让我们验证您是否已成功安装Anaconda。在终端窗口中，输入以下内容：
```sh
conda --version
```
Conda将回复您已安装的版本号，如：conda 3.11.0

注意：如果您看到错误消息，请检查您是否登录到安装Anaconda或Miniconda的帐户，并确保安装后已关闭并重新打开终端窗口。

更新conda到当前版本
接下来，让我们使用conda update命令更新conda：
```sh
conda update conda
```
Conda将比较版本，并让您知道可以安装的内容。它也会告诉你其他将随着更新自动更新或更改的软件包。

如果有较新版本的conda，键入Y进行更新：
```sh
Proceed ([y]/n)? y
conda更新完成后，来看下一个主题。
```
**4.2 管理环境**
现在让我们通过创建几个环境，然后在它们之间移动来认识环境。

创建并激活环境
使用conda create命令，后跟任何你想调用它的名称：
```sh
conda create --name snowflakes biopython
```
这将创建一个名为/envs/snowflakes的环境，该环境包括程序Biopython。

提示：两个破折号（--）后面的许多常用选项可以缩写为短划线和第一个字母。所以--name和-n选项是一样的，--envs和-e是一样的。见conda --help或conda -h查看缩写列表。

* 激活新环境：

Linux，OS X：source activate snowflakes
Windows：activate snowflakes
提示：默认情况下，环境安装在conda目录下的envs目录中。您可以指定不同的路径。有关详细信息，请参见conda create --help。

提示：由于我们没有指定Python版本，conda安装的版本与安装conda时使用的Python版本一致。

* 创建第二个环境
这次让我们创建和命名一个新的环境，并安装不同版本的Python和两个包命名为Astroid和Babel：
```sh
conda create --name bunnies python=3 astroid babel
```
这将创建第二个新的环境，名为 /envs/bunnies，且包含Python3和Astroid、Babel。

提示：在此环境中应该同时安装所需的所有程序。一次只安装一个可能导致依赖冲突。

提示：您可以在conda创建命令中添加更多信息，输入conda create --help查看详细信息。

列出所有环境
现在让我们检查到目前为止已经安装了哪些环境。使用conda environment info命令找出：
```sh
conda info --envs
```
您将看到如下所示的环境列表：

```sh
conda environments:
    snowflakes      */home/username/miniconda/envs/snowflakes
    bunnies          /home/username/miniconda/envs/bunnies
    root             /home/username/miniconda
```
验证当前环境
你现在使用哪个环境呢 —— snowflakes 还是 bunnies？可以输入同样的命令来查看：
```sh
conda info --envs
```
Conda显示所有环境的列表，当前环境显示在前面的提示（括号）或[括号]中：

(snowflakes)
注意：conda还在您的环境列表中的活动环境前放置星号（*）;请参阅上面的“列出所有环境”。

切换到其他环境（激活/停用）
更改为其他环境，输入以下命令：

Linux，OS X：source activate bunnies
Windows：activate bunnies
将当前环境的路径更改回root：

Linux，OS X：source deactivate
Windows：deactivate
提示：当环境取消激活时，(bunnies)将不再显示在提示中。

制作环境的完整副本
通过创建环境的克隆来创建环境的精确副本。这里我们将克隆snowflakes创建一个名为flowers的精确副本：
```sh
conda create --name flowers --clone snowflakes
```
检查生成的副本：
```sh
conda info --envs
```
您现在应该看到列出的三个环境：flowers，bunnies和snowflakes。

删除环境
如果你真的不想要一个名为flowers的环境，只需删除它如下：
```sh
conda remove --name flowers --all
```

要验证flowers环境现在已删除，请键入命令：
```sh
conda info --envs
```
flowers不再在你的环境列表中，所以我们知道它被删除。

了解有关环境的详情
要了解有关任何conda命令的更多信息，只需在键入命令后跟--help：
```sh
conda remove --help
.. _managing-python：
```
**4.3 管理Python**
Conda处理Python与任何其他包相同，所以它很容易管理和更新多个安装。

检查Python版本
首先让我们检查一下可以安装哪些版本的Python：
```sh
conda search --full-name python
```
你可以使用conda search python来显示名字中包含的所有包
文本python或添加--full-name选项来指定。

安装不同版本的Python
假如你需要Python3来学习编程，但你不想通过更新来覆盖你的Python2.7环境。你可以创建并激活名为snakes的新环境，然后安装最新版本的Python3，命令如下：
```sh
conda create --name snakes python=3
Linux，OS X：source activate snakes
Windows：activate snakes
```
提示：明智的做法是将这个环境命名为python这样的描述性名称。

验证添加的环境
要验证是否已添加了snakes环境，请键入以下命令：
```sh
conda info --envs
```
Conda显示所有环境的列表，当前环境显示在前面的提示中的（括号）或[括号]里：

(snakes)
在新环境中验证Python版本
验证snakes环境使用Python3版本：
```sh
python --version
```
使用不同版本的Python
要切换到新环境使用不同版本的Python，只需要激活它。让我们切换回默认值，2.7：

Linux，OS X：source activate snowflakes
Windows：activate snowflakes
在环境中验证Python版本
验证snowflakes环境是否使用安装conda时使用的相同Python版本：

python --version
停用此环境
在雪花环境中完成工作后，停用此环境
将您的PATH恢复到之前的状态：

Linux，OS X：source deactivate
Windows：deactivate
**4.4 管理包**
我们来认识包。当我们创建一个新的环境时（Astroid，Babel和一个具体的版本的Python），我们已经安装了几个包。我们将检查我们有什么包，检查什么是可用的，查找特定的包并安装它。然后我们会查找并安装存在于Anaconda.org存储库中的包，安装更使用pip install的包，以及安装一个商业包。

查看在环境中安装的软件包和版本的列表
使用此选项可查看环境中安装的是哪个版本的Python或其他程序，或者确认已添加或删除了包。在您的终端窗口中，只需键入：
```sh
conda list
```
**
用conda install命令查看使可用的软件包列表

可用于conda安装的软件包列表（按Python版本排序）可从http://docs.continuum.io/anaconda/pkg-docs.html得到。

搜索包

首先让我们检查一下我们想要的软件包是否可供conda安装：
```sh
conda search beautifulsoup4
```
这将显示包，因此我们知道它是可用的。

安装新软件包

我们将在当前环境中安装Beautiful Soup，使用conda安装如下：
```sh
conda install --name bunnies beautifulsoup4
```
注意：你必须告诉conda环境的名称（--name bunnies），否则它将安装在当前环境。

现在激活bunnies环境，并做一个conda列表看到安装的新程序：

Linux，OS X：source activate bunnies
Windows：activate bunnies
所有平台：
```sh
conda list
```
从Anaconda.org安装软件包
对于使用conda install不可用的软件包，我们接下来看看Anaconda.org。Anaconda.org是一个用于公共和私人包存储库的包管理服务。Anaconda.org是Continuum Analytics产品，就像Anaconda和Miniconda。

提示：您不需要注册到Anaconda.org下载文件。

要从Anaconda.org下载到当前环境，我们将通过键入我们想要的包的完整的URL来指定Anaconda.org作为“通道”。

在浏览器中，转到http://anaconda.org。我们正在寻找一个名为“bottleneck”的包，在左上角名为“Search Anaconda Cloud”的框中，输入“bottleneck”，然后单击“Search”按钮。

在Anaconda.org上有十多个bottleneck可用，但我们想要的最多下载量的副本。因此，你可以通过点击“下载”标题按下载数量进行排序。

通过单击软件包名称选择下载量最多的版本。这将带您到Anaconda.org详细信息页面，其中显示用于下载的确切命令：

conda install --channel https://conda.anaconda.org/pandas bottleneck
检查包下载是否正确
```sh
conda list
```
使用pip安装软件包
对于conda或Anaconda.org不提供的软件包，我们经常可以使用pip（“pip installs packages”的缩写）来安装软件包。

提示：Pip只是一个包管理器，所以它不能为您管理环境。 Pip甚至不能更新Python，因为不像conda，它不把Python当做一个包。但它确实安装了一些conda没有的东西。 pip和conda都包括在Anaconda和Miniconda。

我们激活想放置程序的环境，然后用pip安装一个名为“See”的程序：

Linux，OS X：source activate bunnies
Windows：activate bunnies
所有平台：
```sh
pip install see
```
验证pip安装

检查看是否已安装：
```sh
conda list
```
安装商业包
安装商业包与用conda安装任何其他包相同。因此，作为示例，让我们安装，然后删除Continuum的商业包IOPro的试用版，这可以加速你的Python处理：
```sh
conda install iopro
```
提示：除了学术用途，此免费试用期在30天后过期。

现在，您可以使用conda命令，从Anaconda.org下载或使用pip install安装和验证任何您想使用conda的软件包，无论是开源还是商业。

**4.5 删除软件包，环境或conda**
让我们结束这个测试，通过删除一个或多个测试包，环境或conda。

删除包
如果你决定不继续使用商业包IOPro，您可以从bunnies环境中删除它：
```sh
conda remove --name bunnies iopro
```
确认程序已删除

使用conda列表确认IOPro已被删除：
```sh
conda list
```
删除环境
我们不再需要snakes环境，因此输入命令：
```sh
conda remove --name snakes --all
```
验证环境已删除

要验证蛇的环境现在已被删除，请键入命令：
```sh
conda info --envs
```
Snakes不再显示在环境列表中，因此我们知道它已被删除。

删除conda
Linux，OS X：
删除Anaconda或Miniconda安装目录：
```sh
rm -rf ~/miniconda OR  rm -rf ~/anaconda
```
Windows：转到控制面板，单击“添加或删除程序”，选择“Python 2.7（Anaconda）”或“Python 2.7 Miniconda”），然后单击删除程序。
更多资源
要读取任何conda命令的完整文档，请键入命令,后面加-h代表“帮助”。例如，了解conda更新命令：conda update -h
完整文档：https://conda.io/docs/
Cheat sheet: Conda cheat sheet
常见问题：http://docs.continuum.io/anaconda/faq.html 和 FAQ
免费社区支持：https://groups.google.com/a/continuum.io/forum/#!forum/anaconda
付费支持选项：http://continuum.io/support
Continuum Analytics培训与咨询：Continuum Analytics提供Python培训课程。我们的教学理念是，最好的学习方法是对现实世界问题的亲身体验。课程可在线，在许多网站上，或在您的营业地点内部。我们还为科学和业务数据的分析，管理和可视化提供咨询服务，或者在现代硬件和GPU上优化您的处理工作流程。
未完待续......