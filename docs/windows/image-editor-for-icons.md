---
title: （c + +） 图标的图像编辑器
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: 782462a4aeba72252c4d6043bd192f6892a3966f
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336574"
---
# <a name="image-editor-for-icons-c"></a>（c + +） 图标的图像编辑器

单击解决方案资源管理器的图像文件 （如.ico、.bmp、.png），图像将图像编辑器中打开方式在代码编辑器中打开代码文件完全相同。 图像编辑器选项卡处于活动状态，可以看到与用于创建和编辑映像的许多工具工具栏。 以及位图、 图标和光标，你可以编辑 GIF 或 JPEG 格式上使用命令的图像**图像**菜单和上的工具**图像编辑器**工具栏。

图形资源是为应用程序定义的映像。 可以手工绘制或绘制使用的形状。 可以选择编辑、 翻转或调整其大小的图像的部分也可以从所选映像的一部分创建自定义画笔，并用此画笔绘制。 可以定义图像属性、 将映像保存在不同的格式，并将图像从一种格式转换为另一个。

除了创建新的图形资源，你可以[导入现有的映像](../windows/how-to-import-and-export-resources.md)进行编辑，然后将其添加到你的项目。 也可以打开并编辑映像不是用于项目的一部分[独立图像编辑](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)。

> [!NOTE]
> 使用**的图像编辑器**，可以查看 32 位映像，但不能编辑这些。

使用图像编辑器，可以执行下列操作：

- [处理颜色](../windows/working-with-color-image-editor-for-icons.md)

- [处理图标和光标：显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [使用图像编辑器命令的快捷键](../windows/accelerator-keys-image-editor-for-icons.md)

**的图像编辑器**窗口中显示的图像，并用一个拆分条分隔两个窗格的两个视图。 你可以将拆分条从一端拖动到另一端来更改窗格的相对大小。 活动窗格将显示选择边框。

**的图像编辑器**窗口可以进行调整以适合您的需要和首选项。 你可以 [更改放大因子](../windows/changing-the-magnification-factor-image-editor-for-icons.md) 以及 [显示或隐藏像素网格](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)。

> [!NOTE]
> 使用**的图像编辑器**，可以查看 32 位映像，但不能编辑这些。

## <a name="image-menu"></a>“图像”菜单

**图像**时才会显示菜单**映像**编辑器处于活动状态，具有命令，用于编辑映像、 管理调色板，以及设置**的图像编辑器**窗口选项。 此外，使用设备映像的命令是可用时使用的图标和光标。

|命令|描述|
|---|---|
|**反转颜色**|反转颜色。 有关详细信息，请参阅[反转所选内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)。|
|**水平翻转**|水平翻转图像或选定内容。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。|
|**垂直翻转**|垂直翻转图像或选定内容。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。|
|**旋转 90 度**|将图像或选定内容旋转 90 度。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。|
|**显示颜色窗口**|此时将打开[颜色窗口](../windows/colors-window-image-editor-for-icons.md)，在其中可以选择要用于你的映像的颜色。 有关详细信息，请参阅[处理颜色](../windows/working-with-color-image-editor-for-icons.md)。|
|**所选内容用作画笔**|使你能够从图像的一部分创建自定义画笔。 你的选择将成为在图像中分布中所选内容的颜色的自定义画笔。 在拖动路径也会保留所选内容的副本。 您拖动的速度就越慢，进行更多副本。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。|
|**复制和大纲选择**|创建当前选定内容的副本并绘制其轮廓。 如果当前选定内容中包含的背景色，它将被排除在外已[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)选定。
|**调整颜色**|此时将打开[自定义颜色选择器](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)，可用于自定义映像的使用的颜色。 有关详细信息，请参阅[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。|
|**加载调色板**|此时将打开[加载调色板对话框](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)，这样您就可以加载以前保存到.pal 文件的调色板颜色。|
|**保存调色板**|.Pal 文件将保存调色板颜色。|
|**绘制不透明**|选定，将使当前所选内容不透明。 未选中状态，将使当前所选内容透明。 有关详细信息，请参阅[选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|
|**工具栏编辑器**|此时将打开[新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)。|
|**网格设置**|此时将打开**网格设置**映像可以在其中指定网格的对话框。|
|**新建图像类型**|此时将打开[新建\<设备 > 图像类型对话框](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)。 单个图标资源可以包含不同大小的多个映像，windows 可以使用相应的图标大小，具体取决于将如何显示。 新的设备类型不会修改该图标的大小，但而不是创建图标中的新映像。 仅适用于图标和光标。|
|**当前图标/光标图像类型**|将打开子菜单，其中列出了前几个可用的游标或图标映像 （前九个）。 最后一个命令在子菜单，**更多...**，打开[开放\<设备 > 图像对话框的](../windows/open-device-image-dialog-box-image-editor-for-icons.md)。|
|**删除图像类型**|删除所选的设备映像。|
|**工具**|启动包含所有可用工具的子菜单[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)。|

**网格设置**对话框允许您指定映像的网格设置和编辑图像上显示网格线。 行可用于编辑映像，而不保存为图像本身的一部分。

|属性|描述|
|---|---|
|**像素网格**|选中时，图像编辑器中显示一个网格，每个像素周围。 仅在 4 × 及更高分辨率显示网格。|
|**磁贴网格**|选中时，显示的像素为单位的块周围的网格中网格间距值所指定的图像编辑器。|
|**Width**|指定每个磁贴块的宽度。 绘制位图包含按固定间隔排列的多个映像时，此属性很有用。|
|**Height**|指定每个磁贴块的高度。 绘制位图包含按固定间隔排列的多个映像时，此属性很有用。|

## <a name="toolbar"></a>Toolbar

**的图像编辑器**工具栏包含用于绘制、 绘制、 输入文本、 擦除和操作视图的工具。 它还包含选项选择器，可以选择使用每个工具的选项。 例如，你可以选择从各种画笔宽度、 放大因子和行样式。

> [!NOTE]
> 中提供的所有工具**的图像编辑器**工具栏上，还提供从**映像**菜单 (在**工具**命令)。

![图像编辑器工具栏](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")的图像编辑器工具栏

若要使用**的图像编辑器**工具栏和**选项**选择器中，选择的工具或所需选项。

> [!TIP]
> 将鼠标光标悬停工具栏按钮上时，会出现工具提示。 这些提示可以帮助您确定每个按钮的功能。

与**选项**选择器可以指定宽度的线条、 画笔笔画和的详细信息。 上的图标**选项**选择器按钮更改所选具体取决于哪种工具。

![绘制&#45;的图像编辑器工具栏上的形状选择器](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")的图像编辑器工具栏上的选项选择器

### <a name="use-the-text-tool-dialog-box"></a>使用文本工具对话框

使用**文本工具**对话框中，将文本添加到光标、 位图或图标资源。

若要访问此对话框中，打开[的图像编辑器](../windows/window-panes-image-editor-for-icons.md)。 选择**工具**从**映像**菜单，并选择**文本工具**命令。

#### <a name="font-button"></a>字体按钮

此时将打开**文本工具字体**对话框中，可以在其中更改字体、 样式或游标字体的大小。 更改应用于中显示的文本**文本**区域。

若要访问此对话框中，选择**字体**按钮**文本工具**对话框。 可用的属性包括：

|属性|描述|
|---|---|
|**字体**|列出可用的字体。|
|**字形**|列出指定的字体的可用样式。|
|**Size**|列出指定的字体的可用点大小。|
|**示例**|显示文本与指定的字体设置的显示方式的示例。|
|**脚本**|列出了可用的语言脚本对于指定的字体。 时选择不同的语言脚本，该语言的字符集可用于创建多语言文档。|

若要更改图像上文本的字体：

下面的过程是如何将文本添加到 Windows 应用程序中的图标和操作文本的字体的示例。

1. 创建 c + + Windows 窗体应用程序。 有关详细信息，请参阅[创建一个 Windows 应用程序项目](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5)。 *App.ico*默认情况下将文件添加到你的项目。

1. 在中**解决方案资源管理器**，双击该文件*app.ico*。 [的图像编辑器](../windows/image-editor-for-icons.md)将打开。

1. 从**图像**菜单中，选择**工具**，然后选择**文本工具**。 **文本工具**对话框将出现。

1. 在中**文本工具**对话框中，键入*c + +* 空文本区域中。 此文本将显示在一个可调整大小的框，位于左上角*app.ico*，在**图像编辑器**。

1. 在中**的图像编辑器**，将可调整大小框中拖到 app.ico，以提高文本可读性的中心。

1. 在中**文本工具**对话框中，选择**字体**按钮。 **文本工具字体**对话框将出现。

1. 在中**文本工具字体**对话框中，选择**Times New Roman**从列表中列出的可用字体**字体**列表框。

1. 选择**加粗**从列表中列出的可用字体样式**字体样式**列表框。

1. 选择**10**从列表中的可用点中列出的大小**大小**列表框。

1. 选择“确定”按钮。 **文本工具字体**对话框将关闭，并且新的字体设置将应用于您的文本。

1. 选择**关闭**按钮**文本工具**对话框。 在文本周围的调整大小框将不会出现**的图像编辑器**。

#### <a name="text-area"></a>文本区域

显示作为资源的一部分显示的文本。 最初此区域为空。

> [!NOTE]
> 如果**透明背景**，则只将文本将被放入映像。 如果**不透明背景**设置，则填充的边界矩形[背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)，将放置文本的背景。 有关详细信息，请参阅[选择透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

您可以右键单击**文本工具**对话框中，若要访问默认的快捷菜单包含一组标准的 Windows 命令。

### <a name="to-display-or-hide-the-image-editor-toolbar"></a>若要显示或隐藏的图像编辑器工具栏

由于许多绘图工具都可以从[键盘](../windows/accelerator-keys-image-editor-for-icons.md)，有时还是需要隐藏**图像编辑器**工具栏。

上**视图**菜单中，选择**工具栏**然后选择**的图像编辑器**。

   > [!NOTE]
   > 此工具栏中的元素将显示为不可用时的图像文件从当前项目或解决方案不是在中打开**的图像编辑器**。 请参阅[创建图标或其他图像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)，用于将图像文件添加到你的项目信息。

## <a name="window-panes"></a>窗口窗格

**的图像编辑器**窗口通常由拆分栏分隔两个窗格中显示图像。 其中一个视图是实际大小和其他被放大 （默认的放大因子为 6）。 这两个窗格中的视图会自动更新： 其他立即显示在一个窗格中所做的更改。 两个窗格轻松处理的映像，在其中可以区分单个像素并，同时，观察其对图像的实际大小视图所做的工作的影响的放大视图。

左窗格中使用所需空间 (最多一半**图像**窗口) 以显示你的映像的 1:1 放大视图 （默认值）。 右窗格显示缩放的图像 （默认情况下 6:1 放大倍数）。 你可以在每个窗格使用放大倍数**Magnify**上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或通过使用加速键。

您可以扩大的较小的窗格**的图像编辑器**窗口并使用两个窗格显示大图像的不同区域。 选择窗格中选择它。

可以通过将指针定位在拆分栏和向右或向左移动拆分条来更改窗格的相对大小。 如果你想要在只有一个窗格中，在拆分栏可以移动到任意一侧。

如果**的图像编辑器**窗格处于放大 4 倍或更高版本，可以显示像素网格在图像中的单个像素的界限。

### <a name="to-change-the-magnification-factor"></a>若要更改放大因子

默认情况下**图像**编辑器以实际大小的左窗格中显示的视图和 6 个在右窗格中的查看时间实际大小。 放大因子 （在工作区底部的状态栏中所示） 是图像的实际大小和显示的大小之间的比率。 默认因子为 6，范围是从 1 到 10。

1. 选择**的图像编辑器**你想要更改其放大因子窗格。

1. 上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)，选择右侧的箭头[放大工具](../windows/toolbar-image-editor-for-icons.md)和从子菜单中选择缩放系数：**1 X**， **2 X**， **6 X**，或**8 X**。

   > [!NOTE]
   > 若要选择中列出的内容中的放大因子**Magnify**工具中，使用加速键。

### <a name="to-display-or-hide-the-pixel-grid"></a>若要显示或隐藏像素网格

为所有**的图像编辑器**放大因子为 4 或更高版本的窗格，可以显示一个网格在图像中的单个像素的界限。

1. 上**图像**菜单中，选择**网格设置**。

1. 选择**像素网格**复选框以显示网格中，或清除相应的框以隐藏网格。

> [!TIP]
> 将鼠标光标悬停工具栏按钮上时，会出现工具提示。 这些提示可以帮助您确定每个按钮的功能。

## <a name="visual-studio-image-library"></a>Visual Studio 图像库

可以免费下载**Visual Studio 图像库**，其中包含许多动画、 位图和图标可以在你的应用程序中使用。 有关如何下载库的详细信息，请参阅 [Visual Studio 图像库](/visualstudio/designers/the-visual-studio-image-library)。

## <a name="managed-resources"></a>托管资源

可以使用**图像**编辑器并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[图标](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)