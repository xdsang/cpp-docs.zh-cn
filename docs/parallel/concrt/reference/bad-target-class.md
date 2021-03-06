---
title: bad_target 类
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 0440955718bee3b426f5e4625b5eb3fc559a5d28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434478"
---
# <a name="badtarget-class"></a>bad_target 类

此类描述消息块被给予指向目标的指针，但该目标对于正在执行的操作无效时引发的异常。

## <a name="syntax"></a>语法

```
class bad_target : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[bad_target](#ctor)|已重载。 构造 `bad_target` 对象。|

## <a name="remarks"></a>备注

由于尝试使用不同的目标为保留的消息或释放它所持有的保留的目标的原因通常引发此异常。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`bad_target`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> bad_target

构造 `bad_target` 对象。

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)

