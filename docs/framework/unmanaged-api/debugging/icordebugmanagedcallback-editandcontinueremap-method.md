---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: EditAndContinueRemap'
title: Метод ICorDebugManagedCallback::EditAndContinueRemap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: ad8932e41236cdb8ed213024efb4175292a5d5f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791013"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="a9c46-103">Метод ICorDebugManagedCallback::EditAndContinueRemap</span><span class="sxs-lookup"><span data-stu-id="a9c46-103">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="a9c46-104">Этот метод использовать не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="a9c46-104">This method has been deprecated.</span></span> <span data-ttu-id="a9c46-105">Он уведомляет отладчик о том, что событие повторного сопоставления было отправлено в интегрированную среду разработки (IDE).</span><span class="sxs-lookup"><span data-stu-id="a9c46-105">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c46-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a9c46-106">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a9c46-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="a9c46-107">Remarks</span></span>  

 <span data-ttu-id="a9c46-108">`EditAndContinueRemap`Метод вызывается при попыток выполнения кода в старой версии обновленной функции.</span><span class="sxs-lookup"><span data-stu-id="a9c46-108">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="a9c46-109">Среда CLR вызывает `EditAndContinueRemap` метод для отправки события повторного сопоставления в интегрированную среду разработки.</span><span class="sxs-lookup"><span data-stu-id="a9c46-109">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9c46-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a9c46-110">Requirements</span></span>  

 <span data-ttu-id="a9c46-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9c46-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9c46-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9c46-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9c46-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9c46-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9c46-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9c46-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c46-115">См. также</span><span class="sxs-lookup"><span data-stu-id="a9c46-115">See also</span></span>

- [<span data-ttu-id="a9c46-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a9c46-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
