---
title: 编译器错误 C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 435288ba657bd22ba29c6681014ae15baa051cec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636457"
---
# <a name="compiler-error-c3909"></a>编译器错误 C3909

aWinRT 或托管的事件的声明必须出现在 WinRT 或托管的类型

Windows 运行时事件或托管事件是在本机类型中声明的。 要修复此错误，请在 Windows 运行时类型或托管类型中声明事件。

有关详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。

下面的示例生成 C3909，并演示如何修复此错误：

```
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```