---
title: 编译器警告 （等级 1） C4083
ms.date: 11/04/2016
f1_keywords:
- C4083
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
ms.openlocfilehash: 854d4a9887b8a9ada12adc94509745458a1e9523
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516372"
---
# <a name="compiler-warning-level-1-c4083"></a>编译器警告 （等级 1） C4083

预期 token;找到标识符 identifier

在中错误的位置发生标识符 **#pragma**语句。

## <a name="example"></a>示例

```
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

检查的语法[#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)指令。