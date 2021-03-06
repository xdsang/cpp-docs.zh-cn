---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
apiname:
- _CrtMemCheckpoint
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: ee435ba3e9e40795280dee0f97feaad32c8b0fc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589505"
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint

获取调试堆的当前状态并将存储在应用程序提供 **_CrtMemState**结构 （仅限调试版本）。

## <a name="syntax"></a>语法

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>参数

*state*<br/>
指向 **_CrtMemState**结构填充内存检查点。

## <a name="remarks"></a>备注

**_CrtMemCheckpoint**函数在任意给定时刻创建调试堆的当前状态的快照。 此快照可由其他堆状态函数（如 [_CrtMemDifference](crtmemdifference.md) ）用来帮助检测内存泄漏和其他问题。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtMemState**在预处理过程中删除。

应用程序必须将一个指针传递给先前分配的实例 **_CrtMemState**中按照 crtdbg.h 所定义的结构*状态*参数。 如果 **_CrtMemCheckpoint**遇到的错误检查点创建期间，该函数将生成 **_CRT_WARN**调试报表描述出现的问题。

有关详细信息，有关堆状态函数和 **_CrtMemState**结构，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*状态*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为**EINVAL**并返回该函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>、\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** 仅限 UCRT 的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
