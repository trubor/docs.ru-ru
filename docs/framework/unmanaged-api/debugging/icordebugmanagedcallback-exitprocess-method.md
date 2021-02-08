---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: ExitProcess'
title: Метод ICorDebugManagedCallback::ExitProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 3418931b8397edefcb801986275c35b28e00072d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790962"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="8f21e-103">Метод ICorDebugManagedCallback::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="8f21e-103">ICorDebugManagedCallback::ExitProcess Method</span></span>

<span data-ttu-id="8f21e-104">Уведомляет отладчик о завершении процесса.</span><span class="sxs-lookup"><span data-stu-id="8f21e-104">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f21e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f21e-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f21e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8f21e-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="8f21e-107">окне Указатель на объект ICorDebugProcess, представляющий процесс.</span><span class="sxs-lookup"><span data-stu-id="8f21e-107">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f21e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f21e-108">Remarks</span></span>  

 <span data-ttu-id="8f21e-109">Невозможно продолжить выполнение `ExitProcess` события.</span><span class="sxs-lookup"><span data-stu-id="8f21e-109">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="8f21e-110">Это событие может вызываться асинхронно для других событий, пока процесс остановлен.</span><span class="sxs-lookup"><span data-stu-id="8f21e-110">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="8f21e-111">Это может произойти, если процесс завершается при остановке, обычно из-за некоторой внешней силы.</span><span class="sxs-lookup"><span data-stu-id="8f21e-111">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="8f21e-112">Если общеязыковая среда выполнения (CLR) уже передает управляемый обратный вызов, это событие будет отложено до тех пор, пока этот обратный вызов не вернется.</span><span class="sxs-lookup"><span data-stu-id="8f21e-112">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="8f21e-113">`ExitProcess`Событие является единственным событием Exit/unload, которое гарантированно вызывается при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="8f21e-113">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f21e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8f21e-114">Requirements</span></span>  

 <span data-ttu-id="8f21e-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f21e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f21e-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f21e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f21e-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f21e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f21e-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f21e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f21e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8f21e-119">See also</span></span>

- [<span data-ttu-id="8f21e-120">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="8f21e-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
