---
title: UI 支持类 (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.ui
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
ms.openlocfilehash: 7306ddbbc3cf70850e0c7c66e48abf402017e5db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644216"
---
# <a name="ui-support-classes"></a>UI 支持类

下面的类提供常规的 UI 支持：

- [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) Microsoft HTML 分析和呈现引擎的接口。

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md)为通过该容器进行通信的主要方法提供了一个控件。 管理激活和停用的就地控件。

- [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)管理就地控件重新激活。 使无窗口控件以接收消息，以及若要参与拖放操作。

- [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md)协助就地控件与其容器之间的通信。

- [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md)使控件以显示本身直接和以通知容器中显示的更改。 提供无闪烁的绘图、 非矩形的透明控件和命中测试的支持。

## <a name="related-articles"></a>相关文章

[ATL 教程](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)

