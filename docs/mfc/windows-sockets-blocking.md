---
title: Windows 套接字：阻止
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 7b41f034e08570e418bf24d9d720795eafc37932
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610569"
---
# <a name="windows-sockets-blocking"></a>Windows 套接字：阻止

本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文包含锁定。 文章中介绍了其他问题： [Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)并[Windows 套接字： 转换字符串](../mfc/windows-sockets-converting-strings.md)。

如果使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，将需要自行管理这些问题。 如果使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 将为您管理它们。

## <a name="blocking"></a>锁定

套接字可以处于“锁定模式”或“非锁定模式”。 处于锁定（或同步）模式的套接字的函数直到可完成其操作才会返回。 这称为“锁定”，因为调用其函数的套接字无法执行任何操作 - 在调用返回之前处于锁定状态。 调用`Receive`成员函数，例如，可能需要任意长的时间才能完成，因为它将等待发送应用程序发送 (这是如果您将`CSocket`，或使用`CAsyncSocket`与阻塞)。 如果`CAsyncSocket`对象处于未锁定模式 （同步操作的），则调用立即返回和当前的错误代码，可检索与[GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror)成员函数，是**WSAEWOULDBLOCK**，，该值指示调用是否已锁定了因为模式未立即返回。 (`CSocket`永远不会返回**WSAEWOULDBLOCK**。 此类为您管理锁定。）

套接字的行为在 32 位和 64 位操作系统下不同（如 Windows 95 或 Windows 98）于在 16 位操作系统下（如 Windows 3.1）。 不同于 16 位操作系统，32 位和 64 位操作系统使用强占式多任务并提供多线程处理。 在 32 位和 64 位操作系统下，您可在单独的辅助线程中放置套接字。 线程中的套接字可在不影响应用程序中其他活动的情况下锁定，并且锁定时不会占用计算机时间。 有关多线程编程的信息，请参阅文章[多线程处理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

> [!NOTE]
>  在多线程应用程序中，您可以使用 `CSocket` 的锁定特性简化程序的设计，而不影响用户界面的响应能力。 通过在主线程处理用户交互并在备用线程中处理 `CSocket`，您可以分隔这些逻辑操作。 在不是多线程的应用程序中，这两个活动必须组合并作为单个线程处理，这通常意味着使用 `CAsyncSocket` 以便您可按需处理通信请求，或重写 `CSocket::OnMessagePending` 以在同步活动期间处理用户操作。

余下的讨论适用于面向 16 位操作系统的程序员：

通常，如果您使用的是 `CAsyncSocket`，则应避免使用锁定操作，应改用异步操作。 在异步操作中，从点接收**WSAEWOULDBLOCK**后调用的错误代码`Receive`，例如，在等待，直到你`OnReceive`成员函数调用以通知您是否可以读取电子邮件了。 异步调用都是通过调用返回套接字的相应回调通知函数，如[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)。

在 Windows 下，锁定调用被视为不良实践。 默认情况下[CAsyncSocket](../mfc/reference/casyncsocket-class.md)支持异步调用，并且您必须管理自己使用回调通知锁定。 类[CSocket](../mfc/reference/csocket-class.md)后，就是同步。 它将为您推送 Windows 消息和管理锁定。

有关锁定的详细信息，请参阅 Windows 套接字规范。 "On"函数的详细信息，请参阅[Windows 套接字： 套接字通知](../mfc/windows-sockets-socket-notifications.md)并[Windows 套接字： 从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)。

有关详细信息，请参见:

- [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)

