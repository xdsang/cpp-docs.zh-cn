---
title: CDefaultHashTraits 类
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: c8896ce27afc40ad095e02a2453628ffc05900da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466139"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits 类

此类提供一个静态函数用于计算哈希值。

## <a name="syntax"></a>语法

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|（静态）调用此函数来计算给定元素的哈希值。|

## <a name="remarks"></a>备注

此类包含返回给定元素的哈希值的单个静态函数。 使用此类[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="hash"></a>  CDefaultHashTraits::Hash

调用此函数来计算给定元素的哈希值。

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>参数

*元素*<br/>
元素。

### <a name="return-value"></a>返回值

返回的哈希值。

### <a name="remarks"></a>备注

默认哈希算法是非常简单： 返回值是元素数。 如果需要更复杂的算法，则重写此函数。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
