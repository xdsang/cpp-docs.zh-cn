---
title: _matherr
ms.date: 04/05/2018
apiname:
- _matherr
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
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: b830dc940fa2abb131f70130033d27b057412137
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329626"
---
# <a name="matherr"></a>_matherr

处理数学错误。

## <a name="syntax"></a>语法

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>参数

*except*<br/>
指向包含错误信息的结构的指针。

## <a name="return-value"></a>返回值

**_matherr**返回 0 以指示错误或一个非零值以指明成功。 如果 **_matherr**返回 0，一条错误消息可以显示并**errno**设置为适当的错误值。 如果 **_matherr**返回非零值，没有错误消息会显示并**errno**保持不变。

有关返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Matherr**函数将处理数学库的浮点函数生成的错误。 这些函数调用 **_matherr**时检测到错误。

对于特定错误处理，可以提供不同的定义 **_matherr**。 如果使用 C 运行时库 (CRT) 的动态链接的版本，可以替换默认 **_matherr**例程中可执行用户定义的版本的客户端。 但是，不能替换默认 **_matherr**例程中的 CRT dll 的 DLL 客户端。

在数学例程中，发生错误时 **_matherr**的指针调用 **_exception**类型结构 (在中定义\<math.h >) 作为参数。 **_exception** 结构包含下列元素。

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

**类型**成员指定数学错误的类型。 它是中定义的以下值之一\<math.h >:

|宏|含义|
|-|-|
| **（_D)** | 自变量域错误 |
| **_SING** | 自变量奇点 |
| **_OVERFLOW** | 溢出范围错误 |
| **_PLOSS** | 基数部分丢失 |
| **_TLOSS** | 基数全部丢失 |
| **_UNDERFLOW** | 结果太小无法表示。 （目前不支持此条件。） |

结构成员 **name** 是指针，指向包含导致错误的函数名称的以 null 结尾的字符串。 结构成员 **arg1** 和 **arg2** 指定导致错误的值。 如果只指定一个自变量，则将它存储在**arg1**。

给定错误的默认返回值为 **retval**。 如果更改返回值，则必须指定是否实际出现了错误。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_matherr**|\<math.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_matherr.c
/* illustrates writing an error routine for math
* functions. The error function must be:
*      _matherr
*/

#include <math.h>
#include <string.h>
#include <stdio.h>

int main()
{
    /* Do several math operations that cause errors. The _matherr
     * routine handles _DOMAIN errors, but lets the system handle
     * other errors normally.
     */
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );
}

/* Handle several math errors caused by passing a negative argument
* to log or log10 (_DOMAIN errors). When this happens, _matherr
* returns the natural or base-10 logarithm of the absolute value
* of the argument and suppresses the usual error message.
*/
int _matherr( struct _exception *except )
{
    /* Handle _DOMAIN errors for log or log10. */
    if( except->type == _DOMAIN )
    {
        if( strcmp( except->name, "log" ) == 0 )
        {
            except->retval = log( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
        else if( strcmp( except->name, "log10" ) == 0 )
        {
            except->retval = log10( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
    }
    printf( "Normal: " );
    return 0;    /* Else use the default actions */
}
```

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
