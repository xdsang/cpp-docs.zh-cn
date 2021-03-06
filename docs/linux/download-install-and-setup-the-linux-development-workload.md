---
title: 在 Visual Studio 中安装 C++ Linux 工作负载
description: 介绍如何在 Visual Studio 中下载、安装和设置用于 C++ 的 Linux 工作负荷。
ms.date: 02/06/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: c01c8ddeeb8439a7610c0f6c7c11b608ab3675d8
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763878"
---
# <a name="download-install-and-setup-the-linux-workload"></a>下载、安装和设置 Linux 工作负载

可以使用 Windows 中的 Visual Studio IDE 来创建、编辑和调试在 Linux 物理计算机、虚拟机或[适用于 Linux 的 Windows 子系统](/windows/wsl/about)上执行的 C++ 项目。 为了实现所有这些方案，请先安装“使用 C++ 的 Linux 开发”工作负荷。

## <a name="visual-studio-setup"></a>Visual Studio 安装程序

1. 在 Windows 搜索框中键入“Visual Studio 安装程序”：![Windows 搜索框](media/visual-studio-installer-search.png)
2. 在“应用”结果下寻找安装程序并双击它。 打开该安装程序后，选择“修改”，然后单击“工作负荷”选项卡。向下滚动到“其他工具集”，然后选择“使用 C++ 的 Linux 开发”工作负荷。

   ![适用于 Linux 开发的 Visual C++ 工作负荷](media/linuxworkload.png)

1. 如果使用 CMake 或目标是 IoT 或嵌入式平台，请转到“使用 C++ 的 Linux 开发”下右侧的“安装详细信息”窗格，展开“可选组件”，然后选择所需的组件。

1. 单击“修改”以继续进行安装。

## <a name="options-for-creating-a-linux-environment"></a>用于创建 Linux 环境的选项

如果还没有 Linux 计算机，则可以在 Azure 上创建 Linux 虚拟机。 有关详细信息，请参阅[快速入门：在 Azure 门户中创建 Linux 虚拟机](/azure/virtual-machines/linux/quick-create-portal)。

Windows 10 上的另一个选项是激活适用于 Linux 的 Windows 子系统。 有关详细信息，请参阅 [Windows 10 安装指南](/windows/wsl/install-win10)。

## <a name="linux-setup-ubuntu"></a>Linux 安装程序：Ubuntu

目标 Linux 计算机必须安装 **openssh-server**、**g++**、**gdb** 和 **gdbserver**，并且必须运行 ssh 守护程序。 需要压缩才能自动将远程标头与本地计算机同步以获得 Intellisense 支持。 如果这些应用程序尚不存在，则可以按如下所述进行安装：

1. 在 Linux 计算机上的 shell 提示符下，运行：

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   由于 sudo 命令，可能会提示你输入 root 密码。  如果是这样，输入密码然后继续。 完成后，可安装所需服务和工具。

1. 通过运行以下命令，确保 ssh 服务在 Linux 计算机上运行：

   `sudo service ssh start`

   这将启动该服务并在后台运行它，准备接受连接。

## <a name="linux-setup-fedora"></a>Linux 安装程序：Fedora

运行 Fedora 的目标计算机使用 dnf 包安装程序。 要下载“openssh-server”、“g++”、“gdb”、“gdbserver”和“zip”并重启 ssh 守护程序，请遵循以下说明：

1. 在 Linux 计算机上的 shell 提示符下，运行：

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   由于 sudo 命令，可能会提示你输入 root 密码。  如果是这样，输入密码然后继续。 完成后，可安装所需服务和工具。

1. 通过运行以下命令，确保 ssh 服务在 Linux 计算机上运行：

   `sudo systemctl start sshd`

   这将启动该服务并在后台运行它，准备接受连接。

