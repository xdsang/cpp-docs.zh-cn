---
title: qsort_s
ms.date: 11/04/2016
apiname:
- qsort_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: 1f0064fd9cf0a3c52456197568adf693fcdaa9a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581865"
---
# <a name="qsorts"></a>qsort_s

执行快速排序。 这是 [qsort](qsort.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增强功能。

## <a name="syntax"></a>语法

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>参数

*base*<br/>
目标数组的开头。

*数量*<br/>
元素中的数组大小。

*width*<br/>
元素大小（字节）。

*compare*<br/>
比较函数。 第一个参数是*上下文*指针。 第二个参数是一个指向*密钥*搜索。 第三个参数是指向要与进行比较的数组元素的指针*密钥*。

*context*<br/>
指向上下文，它可以是任何对象*比较*例程需要访问。

## <a name="remarks"></a>备注

**Qsort_s**函数可实现一种快速排序算法进行排序的数组*数量*，每个元素*宽度*字节。 自变量*基*是指向要进行排序的数组的基的指针。 **qsort_s**使用已排序元素覆盖此数组。 自变量*比较*是指向用户提供的例程，它比较两个数组元素并返回一个值，指定其关系。 **qsort_s**调用*比较*期间排序，将指针传递给两个数组元素，在每次调用例程的一个或多个时间：

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

该例程必须比较这些元素，然后返回下列值之一：

|返回值|描述|
|------------------|-----------------|
|< 0|**elem1**小于**elem2**|
|0|**elem1**等效于**elem2**|
|> 0|**elem1**大于**elem2**|

数组按比较函数中定义的升序进行排序。 若要以降序对数组进行排序，请反转比较函数中的“大于”和“小于”的意义。

如果传递到此函数的参数无效，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回并**errno**设置为**EINVAL**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|密钥|base|compare|num|宽度|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**NULL**|任何|任何|任何|任何|**EINVAL**|
|任何|**NULL**|任何|!= 0|任何|**EINVAL**|
|任何|任何|任何|任何|<= 0|**EINVAL**|
|任何|任何|**NULL**|任何|任何|**EINVAL**|

**qsort_s**具有相同的行为**qsort**却*上下文*参数并设置**errno**。 通过传递*上下文*参数，比较函数可以使用一个对象指针访问对象功能或无法访问其他信息通过一个元素的指针。 添加了*上下文*参数将使得**qsort_s**更加安全，因为*上下文*可用于避免重新进入 bug 引入使用静态变量以使共享信息供*比较*函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h> 和 \<search.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** [CRT 库功能](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

下面的示例演示如何使用*上下文*中的参数**qsort_s**函数。 *上下文*参数使其更方便地执行线程安全排序。 而不是使用必须进行同步以确保线程安全的静态变量，传递不同*上下文*中每个排序的参数。 在此示例中，区域设置对象用作*上下文*参数。

```cpp
// crt_qsort_s.cpp
// compile with: /EHsc /MT
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S in that codepage and \x00a4
// is the n tilde.

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.850"
#define SPANISH_LOCALE "Spanish_Spain.850"
#define ENGLISH_LOCALE "English_US.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S and \x001f for the n tilde.
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.1252"
#define SPANISH_LOCALE "Spanish_Spain.1252"
#define ENGLISH_LOCALE "English_US.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making sort_array vulnerable to thread
// conflicts.

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char s1[256];
    char s2[256];
    strcpy_s(s1, 256, *(char**)str1);
    strcpy_s(s2, 256, *(char**)str2);
    _strlwr_s( s1, sizeof(s1) );
    _strlwr_s( s2, sizeof(s2) );

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(s1,
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);

}

void sort_array(char *array[], int num, locale &loc)
{
    qsort_s(array, num, sizeof(char*), compare, &loc);
}

void print_array(char *a[], int c)
{
   for (int i = 0; i < c; i++)
      printf("%s ", a[i]);
   printf("\n");

}

void sort_german(void * Dummy)
{
   sort_array(array1, 6, locale(GERMAN_LOCALE));
}

void sort_spanish(void * Dummy)
{
   sort_array(array2, 3, locale(SPANISH_LOCALE));
}

void sort_english(void * Dummy)
{
   sort_array(array3, 3, locale(ENGLISH_LOCALE));
}

int main( )
{
   int i;
   HANDLE threads[3];

   printf("Unsorted input:\n");
   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);

   // Create several threads that perform sorts in different
   // languages at the same time.

   threads[0] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_german , 0, NULL));
   threads[1] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_spanish, 0, NULL));
   threads[2] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_english, 0, NULL));

   for (i = 0; i < 3; i++)
   {
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
      {
         printf("Error creating threads.\n");
         exit(1);
      }
   }

   // Wait until all threads have terminated.
   WaitForMultipleObjects(3, threads, true, INFINITE);

   printf("Sorted output: \n");

   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);
}
```

### <a name="sample-output"></a>示例输出

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
