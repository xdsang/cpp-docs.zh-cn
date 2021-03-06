---
title: 如何：将资源包括在编译时 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 06ad2f90e7e72492f1e6ca4000a6c101fc36b205
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320661"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>如何：将资源包括在编译时 （c + +）

通常很简单且方便地使用一个资源脚本 (.rc) 文件中的所有资源的默认安排。 但是，有几个原因，可以将资源置于主.rc 文件之外的文件：

- 若要向保存.rc 文件时将不会删除的资源语句添加注释。

   资源编辑器不直接读取.rc 或`resource.h`文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程，因为不是符号 （例如注释） 的信息将在编译过程中被放弃。 每当.aps 文件与.rc 文件获取同步，重新生成.rc 文件 (例如，保存时，资源编辑器将覆盖.rc 文件和`resource.h`文件)。 对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。

- 若要包括已开发和测试的资源并且无需进一步修改。 （包含在内但没有.rc 扩展名的任何文件不是通过资源编辑器可编辑。）

- 若要包括的正在使用的多个不同项目或，是属于源代码版本控制系统，并因此必须在一个中心位置修改会影响所有项目中存在的资源。

- 包括采用自定义格式的资源（如 RCDATA 资源）。 RCDATA 资源可能具有特殊要求。 例如，您不能使用表达式作为一个值 nameID 字段。 有关详细信息，请参阅 Windows SDK 文档。

## <a name="resource-includes"></a>资源包括

您可以将资源添加其他文件中向当前项目在编译时列出相关**编译时指令**框中**资源包括**对话框。

如果满足下列任一条件的现有.rc 文件中有一些部分，应将部分放在一个或多个单独的.rc 文件并将其包含在你的项目使用**资源包括**对话框。 *Projectname*.rc2 文件创建一个新的项目的 \res 子目录中用于此目的。

可以使用**资源包括**对话框中 c + + 项目以修改将所有资源存储在项目.rc 文件中，所有环境的正常工作安排[符号](../windows/symbols-resource-identifiers.md)在 Resource.h 中。

若要打开**资源包括**对话框中，右键单击.rc 文件中[资源视图](../windows/resource-view-window.md)，然后选择**资源包括**从快捷菜单。 请参阅以下属性：

|属性|描述|
|--|----|
|**符号头文件**|允许更改头文件的名称，头文件是存储资源文件的符号定义的位置。 有关详细信息，请参阅[更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)。|
|**只读符号指令**|可以包含标头文件包含不应在编辑会话期间修改的符号。 例如，可以包括在多个项目间共享的符号文件。 此外也可以包括 MFC.h 文件。 有关详细信息，请参阅[包括共享 （只读） 或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。|
|**编译时指令**|可以包括创建和编辑单独从主资源文件中的资源的资源文件包含编译时指令 （如有条件地包括资源这些指令），或包含自定义格式中的资源。 此外可以使用**编译时指令框**包括标准 MFC 资源文件。|

> [!NOTE]
> 由标记.rc 文件中显示这些文本框中的项`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分别。 有关详细信息，请参阅[TN035:Visual c + + 中使用多个资源文件和头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

对资源文件使用进行了更改后**资源包括**对话框中，你需要关闭.rc 文件并重新打开它以使更改生效。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>编译时在项目中包含资源

1. 将资源置于具有唯一文件名的资源脚本文件中。 不要使用*projectname*.rc，因为此名称是用于主资源脚本文件的文件名。

1. 右键单击.rc 文件 (在[资源视图](../windows/resource-view-window.md))，然后选择**资源包括**从快捷菜单。

1. 在中**编译时指令**框中，添加[#include](../preprocessor/hash-include-directive-c-cpp.md)编译器指令，以在开发环境中在主资源文件中包含新的资源文件。

   采用这种方式包含的文件中的资源会在编译时成为可执行文件的一部分。 在处理项目的主.rc 文件时，他们不是直接可用于编辑或修改。 单独打开包含的.rc 文件。 包含在内但没有.rc 扩展名的任何文件不会通过资源编辑器可编辑。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>若要指定包含对特定资源 （.rc 文件） 的目录

1. 右键单击解决方案资源管理器中的.rc 文件并选择**属性**从快捷菜单。

1. 选择**资源**的左窗格中的节点，并指定任何附加的包含目录**附加包含目录**属性。

### <a name="to-find-symbols-in-resources"></a>在资源中查找符号

1. 从**编辑**菜单中，选择[查找符号](/visualstudio/ide/go-to)。

1. 在中**Find What**框中，从下拉列表中选择以前的搜索字符串或键入想要查找的加速键 (例如， `ID_ACCEL1`)。

   > [!TIP]
   > 若要使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)为你的搜索，必须使用[在文件中查找](/visualstudio/ide/reference/find-command)从**编辑**而不是菜单**查找符号**命令。 若要启用正则表达式，必须具有**使用：正则表达式**中所选的复选框[查找对话框](/visualstudio/ide/finding-and-replacing-text)。 然后，可以选中右侧的向右箭头按钮**查找内容**框，以显示搜索正则表达式的列表。 当从此列表中选择一个表达式时，它将替换中的搜索文本**查找内容**框。

1. 选择任一**查找**选项，然后选择**查找下一个**。

> [!NOTE]
> 无法搜索字符串、快捷键或二进制资源中的符号。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[创建资源](../windows/how-to-create-a-resource-script-file.md)<br/>
[管理资源](../windows/how-to-copy-resources.md)<br/>