---
title: 支持 IDispatch 和 IErrorInfo
ms.date: 11/04/2016
f1_keywords:
- IErrorInfo
- IDispatch
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: ea45f0bdd2363f4392baee049629c55259e45af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502422"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>支持 IDispatch 和 IErrorInfo

可以使用此模板类[IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的默认实现`IDispatch Interface`您的对象上的任何双接口的一部分。

如果您的对象使用`IErrorInfo`接口来报告错误返回到客户端，则您的对象必须支持`ISupportErrorInfo Interface`接口。 此模板类[ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)提供要实现这一点如果只有一个界面，您的对象上生成错误的简便方法。

## <a name="see-also"></a>请参阅

[ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)

