---
title: nonextensible （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 332f61148ccf8cb5816e8bd347181ac9d130a730
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512436"
---
# <a name="nonextensible"></a>nonextensible

指定`IDispatch`实现仅包括属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。

## <a name="syntax"></a>语法

```cpp
[nonextensible]
```

## <a name="remarks"></a>备注

**Nonextensible** c + + 属性具有相同的功能[nonextensible](/windows/desktop/Midl/nonextensible) MIDL 特性。

利用**nonextensible**还要求[oleautomation](oleautomation.md)属性。

## <a name="example"></a>示例

下面的代码演示的一种用途**nonextensible**属性：

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|`dual` 和`oleautomation`，或 `dispinterface`|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)