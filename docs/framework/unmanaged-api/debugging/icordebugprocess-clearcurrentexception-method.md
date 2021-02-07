---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: ClearCurrentException'
title: Метод ICorDebugProcess::ClearCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 6f356078d8d303acb39cbaa500b7592185ad55ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754047"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="465e9-103">Метод ICorDebugProcess::ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="465e9-103">ICorDebugProcess::ClearCurrentException Method</span></span>

<span data-ttu-id="465e9-104">Очищает текущее неуправляемое исключение для данного потока.</span><span class="sxs-lookup"><span data-stu-id="465e9-104">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="465e9-105">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="465e9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="465e9-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="465e9-107">окне Идентификатор потока, в котором будет очищаться текущее неуправляемое исключение.</span><span class="sxs-lookup"><span data-stu-id="465e9-107">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="465e9-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="465e9-108">Remarks</span></span>  

 <span data-ttu-id="465e9-109">Вызывайте этот метод перед вызовом [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , когда поток сообщил о неуправляемом исключении, которое должно игнорироваться отлаживаемым объектом.</span><span class="sxs-lookup"><span data-stu-id="465e9-109">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="465e9-110">Это приведет к удалению необработанных внутренних () и нестандартных событий (OOB) для данного потока.</span><span class="sxs-lookup"><span data-stu-id="465e9-110">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="465e9-111">Все точки останова OOB и одношаговые исключения автоматически очищаются.</span><span class="sxs-lookup"><span data-stu-id="465e9-111">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="465e9-112">Используйте [ICorDebugThread2:: интерцепткуррентексцептион](icordebugthread2-interceptcurrentexception-method.md) для перехвата текущего управляемого исключения в потоке.</span><span class="sxs-lookup"><span data-stu-id="465e9-112">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="465e9-113">Требования</span><span class="sxs-lookup"><span data-stu-id="465e9-113">Requirements</span></span>  

 <span data-ttu-id="465e9-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="465e9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="465e9-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="465e9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="465e9-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="465e9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="465e9-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="465e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
