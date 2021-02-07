---
description: 'Дополнительные сведения о методе: ICorDebugController:: SetAllThreadsDebugState'
title: Метод ICorDebugController::SetAllThreadsDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: 3bce5360833ae18c68bc8d7ea24f0dec7615f7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710742"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="3efc7-103">Метод ICorDebugController::SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="3efc7-103">ICorDebugController::SetAllThreadsDebugState Method</span></span>

<span data-ttu-id="3efc7-104">Задает состояние отладки всех управляемых потоков в процессе.</span><span class="sxs-lookup"><span data-stu-id="3efc7-104">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3efc7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3efc7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3efc7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3efc7-106">Parameters</span></span>  

 `state`  
 <span data-ttu-id="3efc7-107">окне Значение перечисления "Кордебугсреадстате", указывающее состояние потока для отладки.</span><span class="sxs-lookup"><span data-stu-id="3efc7-107">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="3efc7-108">окне Указатель на объект "ICorDebugThread", представляющий поток, исключаемый из параметра состояния отладки.</span><span class="sxs-lookup"><span data-stu-id="3efc7-108">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="3efc7-109">Если это значение равно null, ни один поток не исключен.</span><span class="sxs-lookup"><span data-stu-id="3efc7-109">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3efc7-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="3efc7-110">Remarks</span></span>  

 <span data-ttu-id="3efc7-111">`SetAllThreadsDebugState`Метод может влиять на потоки, которые не видны через [метод енумератесреадс](icordebugcontroller-enumeratethreads-method.md), поэтому потоки, которые были приостановлены с помощью метода, `SetAllThreadsDebugState` необходимо возобновить с помощью `SetAllThreadsDebugState` метода.</span><span class="sxs-lookup"><span data-stu-id="3efc7-111">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3efc7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3efc7-112">Requirements</span></span>  

 <span data-ttu-id="3efc7-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3efc7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3efc7-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3efc7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3efc7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3efc7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3efc7-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3efc7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efc7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="3efc7-117">See also</span></span>
