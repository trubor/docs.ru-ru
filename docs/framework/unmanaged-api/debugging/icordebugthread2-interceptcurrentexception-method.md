---
description: 'Дополнительные сведения о методе: ICorDebugThread2:: Интерцепткуррентексцептион'
title: Метод ICorDebugThread2::InterceptCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 5bf8d3adf6f5e4a24d8fc5abddb72c0c8963c142
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790717"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="beef4-103">Метод ICorDebugThread2::InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="beef4-103">ICorDebugThread2::InterceptCurrentException Method</span></span>

<span data-ttu-id="beef4-104">Позволяет отладчику перехватить текущее исключение в этом потоке.</span><span class="sxs-lookup"><span data-stu-id="beef4-104">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beef4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="beef4-105">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beef4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="beef4-106">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="beef4-107">окне Указатель на объект ICorDebugFrame, представляющий активный кадр стека.</span><span class="sxs-lookup"><span data-stu-id="beef4-107">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beef4-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="beef4-108">Remarks</span></span>  

 <span data-ttu-id="beef4-109">`InterceptCurrentException`Метод может быть вызван между обратным вызовом исключения ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) или [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) и связанным вызовом [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="beef4-109">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beef4-110">Требования</span><span class="sxs-lookup"><span data-stu-id="beef4-110">Requirements</span></span>  

 <span data-ttu-id="beef4-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beef4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beef4-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beef4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beef4-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beef4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beef4-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beef4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
