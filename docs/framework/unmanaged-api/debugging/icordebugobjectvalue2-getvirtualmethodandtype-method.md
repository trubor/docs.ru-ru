---
description: 'Дополнительные сведения о методе: ICorDebugObjectValue2:: GetVirtualMethodAndType'
title: Метод ICorDebugObjectValue2::GetVirtualMethodAndType
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
ms.openlocfilehash: 73866cc902d60316e3f1f31a86473116c0bff129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781926"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="04973-103">Метод ICorDebugObjectValue2::GetVirtualMethodAndType</span><span class="sxs-lookup"><span data-stu-id="04973-103">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>

<span data-ttu-id="04973-104">Этот метод еще не реализован.</span><span class="sxs-lookup"><span data-stu-id="04973-104">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04973-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04973-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="04973-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="04973-106">Remarks</span></span>  

 <span data-ttu-id="04973-107">Получает указатели интерфейса на экземпляры "ICorDebugFunction" и "ICorDebugType", представляющие самый производный метод и тип для указанной ссылки на элемент.</span><span class="sxs-lookup"><span data-stu-id="04973-107">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04973-108">См. также</span><span class="sxs-lookup"><span data-stu-id="04973-108">See also</span></span>
