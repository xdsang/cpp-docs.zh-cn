---
title: setbuf
ms.date: 11/04/2016
apiname:
- setbuf
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 3b5fbccd304d406131b0c4f7d16a289f80484642
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440491"
---
# <a name="setbuf"></a>setbuf

控制流缓冲。 此函数已弃用；请改用 [setvbuf](setvbuf.md)。

## <a name="syntax"></a>语法

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

*buffer*<br/>
用户分配的缓冲区。

## <a name="remarks"></a>备注

**Setbuf**函数控制缓冲*流*。 *流*参数必须引用打开的文件的已读取或写入。 如果*缓冲区*自变量是**NULL**，流是无缓冲。 如果不是，缓冲区必须指向字符数组的长度**BUFSIZ**，其中**BUFSIZ**是 STDIO 中定义的缓冲区大小。H. 用户指定的缓冲区（而不是给定流的默认系统分配的缓冲区）用于 I/O 缓存。 **Stderr**流是无缓冲的默认值，但你可以使用**setbuf**若要将分配到的缓冲区**stderr**。

**setbuf**已被取代[setvbuf](setvbuf.md)，对于新代码的首选例程。 **setbuf**保留与现有代码的兼容性。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
