---
description: 'Дополнительные сведения о методе ICorDebug:: Terminate'
title: Метод ICorDebug::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: c2de27a47bfd4c364a09180c75109679234f3cae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754294"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="db17d-103">Метод ICorDebug::Terminate</span><span class="sxs-lookup"><span data-stu-id="db17d-103">ICorDebug::Terminate Method</span></span>

<span data-ttu-id="db17d-104">Завершает `ICorDebug` объект.</span><span class="sxs-lookup"><span data-stu-id="db17d-104">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db17d-105">`Terminate` не следует вызывать, пока не получен обратный вызов [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) для всех отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="db17d-105">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db17d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db17d-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="db17d-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="db17d-107">Remarks</span></span>  

 <span data-ttu-id="db17d-108">`Terminate` должен вызываться, когда `ICorDebug` объект больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="db17d-108">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db17d-109">Требования</span><span class="sxs-lookup"><span data-stu-id="db17d-109">Requirements</span></span>  

 <span data-ttu-id="db17d-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db17d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db17d-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db17d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db17d-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db17d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db17d-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db17d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db17d-114">См. также</span><span class="sxs-lookup"><span data-stu-id="db17d-114">See also</span></span>

- [<span data-ttu-id="db17d-115">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="db17d-115">ICorDebug Interface</span></span>](icordebug-interface.md)
