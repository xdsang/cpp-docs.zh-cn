---
title: _read
ms.date: 02/13/2019
apiname:
- _read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: 40f52ea37ae5419fe986aa505aad4fddfe8403ff
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264785"
---
# <a name="read"></a>_read

从文件读取数据。

## <a name="syntax"></a>语法

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>参数

*fd*<br/>
引用打开的文件的文件说明符。

*buffer*<br/>
数据的存储位置。

*buffer_size*<br/>
要读取的字节的最大数目。

## <a name="return-value"></a>返回值

**_read**返回读取，这可能会更少的字节数比*buffer_size*如果少于*buffer_size*字节留在文件中，或如果在文本模式下打开文件。 在文本模式下，每个回车符-换行符对`\r\n`使用单一的换行的字符替换`\n`。 在返回值中仅计算单个换行符。 此替换不影响文件指针。

如果函数尝试在文件末尾进行读取，则返回 0。 如果*fd*是无效，该文件未打开供读取，或文件被锁定，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回-1 并设置**errno**到**EBADF**。

如果*缓冲区*是**NULL**，或者，如果*buffer_size* > **INT_MAX**，将调用无效参数处理程序。 如果允许继续执行，该函数返回-1 和**errno**设置为**EINVAL**。

有关于此代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Read**函数中读取的最大*buffer_size*字节*缓冲区*从与关联的文件*fd*。 读取操作从与给定文件相关联的文件指针的当前位置开始执行。 读取操作完成后，文件指针将指向下一个未读取的字符。

如果文件已在文本模式下打开，读取将终止时 **_read**遇到 CTRL + Z 字符，被视为文件尾指示符。 使用 [_lseek](lseek-lseeki64.md) 可清除文件尾指示符。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_read**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crtreadtxt"></a>输入：crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>输出

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
