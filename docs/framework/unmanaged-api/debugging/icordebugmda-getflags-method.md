---
description: 'Дополнительные сведения о методе: ICorDebugMDA:: "Flags"'
title: Метод ICorDebugMDA::GetFlags
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 53476da06252771627d4883ef9056eb7f945e1b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801180"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="8a1f3-103">Метод ICorDebugMDA::GetFlags</span><span class="sxs-lookup"><span data-stu-id="8a1f3-103">ICorDebugMDA::GetFlags Method</span></span>

<span data-ttu-id="8a1f3-104">Возвращает флаги, связанные с помощником по отладке управляемого кода (MDA), представленным [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8a1f3-104">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a1f3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a1f3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a1f3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a1f3-106">Parameters</span></span>  

 `pFlags`  
 <span data-ttu-id="8a1f3-107">окне Побитовое сочетание значений перечисления [кордебугмдафлагс](cordebugmdaflags-enumeration.md) , определяющих параметры флагов для этого MDA.</span><span class="sxs-lookup"><span data-stu-id="8a1f3-107">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a1f3-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8a1f3-108">Requirements</span></span>  

 <span data-ttu-id="8a1f3-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a1f3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a1f3-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a1f3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a1f3-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a1f3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a1f3-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a1f3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1f3-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8a1f3-113">See also</span></span>

- [<span data-ttu-id="8a1f3-114">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="8a1f3-114">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="8a1f3-115">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="8a1f3-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
