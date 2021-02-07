---
description: 'Дополнительные сведения о методе: ICorDebugValueBreakpoint:: GetValue'
title: Метод ICorDebugValueBreakpoint::GetValue
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
ms.openlocfilehash: b690ea7a39ac70edd8e3e6be7682bae1e808555d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690175"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="048a3-103">Метод ICorDebugValueBreakpoint::GetValue</span><span class="sxs-lookup"><span data-stu-id="048a3-103">ICorDebugValueBreakpoint::GetValue Method</span></span>

<span data-ttu-id="048a3-104">Возвращает указатель интерфейса на объект "ICorDebugValue", представляющий значение объекта, для которого задана точка останова.</span><span class="sxs-lookup"><span data-stu-id="048a3-104">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="048a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="048a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="048a3-106">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="048a3-107">заполняет Указатель на адрес `ICorDebugValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="048a3-107">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048a3-108">Требования</span><span class="sxs-lookup"><span data-stu-id="048a3-108">Requirements</span></span>  

 <span data-ttu-id="048a3-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="048a3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="048a3-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="048a3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="048a3-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="048a3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="048a3-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048a3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048a3-113">См. также</span><span class="sxs-lookup"><span data-stu-id="048a3-113">See also</span></span>
