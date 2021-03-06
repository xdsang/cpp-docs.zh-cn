---
title: 编译器错误 C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 19b9c5a54bf405114bd4d596c2a2cc4708aadcc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507904"
---
# <a name="compiler-error-c2712"></a>编译器错误 C2712

> 无法在要求对象展开的函数中使用 __try

## <a name="remarks"></a>备注

如果您使用，则会发生错误 C2712 [/EHsc](../../build/reference/eh-exception-handling-model.md)，并且带有结构化的异常处理的函数具有需要展开 （析构） 的对象。

可能的解决方案：

- 将要求 SEH 的代码移动到另一个函数中

- 重写使用 SEH 的函数以避免使用具有析构函数的局部变量和参数。 在构造函数或析构函数中不要使用 SEH

- 不使用 /EHsc 进行编译

如果调用通过使用声明的方法，也可能发生错误 C2712 [__event](../../cpp/event.md)关键字。 因为事件可能在多线程环境中使用，编译器将生成代码的阻止操作的基础事件对象，然后将生成的代码封装到 SEH [try-finally 语句](../../cpp/try-finally-statement.md)。 因此，如果调用事件方法并按值传递其类型具有析构函数的自变量，则将发生错误 C2712。 这种情况的一种解决方法是将自变量作为常数引用进行传递。

如果使用进行编译，也会发生 C2712 **/clr: pure** ，并声明静态数组中的函数指针的`__try`块。 静态成员要求编译器下使用动态初始化 **/clr: pure**，这意味着 c + + 异常处理。 但是，不允许在 `__try` 块中进行 C++ 异常处理。

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

## <a name="example"></a>示例

下面的示例生成 C2712，并演示如何修复此错误。

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```