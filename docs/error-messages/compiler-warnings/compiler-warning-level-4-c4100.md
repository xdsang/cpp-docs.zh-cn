---
title: 编译器警告（等级 4）C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 84a0b27203cd43e8a8992c4ba599f1400c6909ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50634858"
---
# <a name="compiler-warning-level-4-c4100"></a>编译器警告（等级 4）C4100

identifier： 未引用的形参

函数的正文中未引用的形式参数。 将忽略未引用的参数。

当代码调用析构函数上时，也可能发出 C4100 未引用的基元类型的参数。  这是 Visual c + + 编译器的限制。

下面的示例生成 C4100:

```
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```