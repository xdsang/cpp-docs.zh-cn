---
title: 编译器错误 C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 15f9ba62751d9b3cb17ab56659310292dab41adf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596776"
---
# <a name="compiler-error-c2588"></a>编译器错误 C2588

:: ~ 标识符： 非法的全局析构函数

析构函数之外类、 结构或联合定义的内容。 这是不允许的。

此错误可能由缺少的类、 结构或联合名称左侧的作用域解析 (`::`) 运算符。

下面的示例生成 C2588:

```
// C2588.cpp
~F();   // C2588
```