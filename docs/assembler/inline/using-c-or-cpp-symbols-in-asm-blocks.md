---
title: 在 __asm 块中使用 C 或 C++ 符号
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: fc22af8ec04d616eb8f5566b118e19c405605401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552511"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>在 __asm 块中使用 C 或 C++ 符号

**Microsoft 专用**

`__asm` 块可以引用块显示范围内的任何 C 或 C++ 符号。 （C 和 C++ 符号是变量名、函数名和标签；即不是符号常量或 `enum` 成员的名称。 您不能调用 C++ 成员函数。）

C 和 C++ 符号的使用有一些限制：

- 每个汇编语言语句只能包含一个 C 或 C++ 符号。 多个符号可以出现在仅使用相同的程序集指令**长度**，**类型**，并**大小**表达式。

- `__asm` 块中引用的函数必须在程序中及早声明（原型化）。 否则，编译器无法区分 `__asm` 块中的函数名和标签。

- `__asm` 块不能使用与 MASM 保留字具有相同的拼写（无论大小写）的任何 C 或 C++ 符号。 MASM 保留字包括指令名称如下所述**推送**和注册名称如 SI。

- 结构和联合标记在 `__asm` 块中无法识别。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>