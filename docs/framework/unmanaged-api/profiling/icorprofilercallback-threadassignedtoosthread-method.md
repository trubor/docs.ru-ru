---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ThreadAssignedToOSThread'
title: Метод ICorProfilerCallback::ThreadAssignedToOSThread
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 04fba4cabb0ac58b3afeaae1fd579865335a9e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647990"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="f9ff5-103">Метод ICorProfilerCallback::ThreadAssignedToOSThread</span><span class="sxs-lookup"><span data-stu-id="f9ff5-103">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>

<span data-ttu-id="f9ff5-104">Уведомляет профилировщик о том, что управляемый поток реализуется с помощью определенного потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="f9ff5-104">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ff5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f9ff5-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9ff5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f9ff5-106">Parameters</span></span>  

 `managedThreadId`  
 <span data-ttu-id="f9ff5-107">окне Идентификатор управляемого потока.</span><span class="sxs-lookup"><span data-stu-id="f9ff5-107">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="f9ff5-108">окне Идентификатор потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="f9ff5-108">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9ff5-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9ff5-109">Remarks</span></span>  

 <span data-ttu-id="f9ff5-110">`ThreadAssignedToOSThread`Обратный вызов существует, чтобы профилировщик мог поддерживать точное сопоставление по волокнам потоков операционной системы с управляемыми потоками.</span><span class="sxs-lookup"><span data-stu-id="f9ff5-110">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ff5-111">Требования</span><span class="sxs-lookup"><span data-stu-id="f9ff5-111">Requirements</span></span>  

 <span data-ttu-id="f9ff5-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9ff5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ff5-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9ff5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9ff5-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9ff5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9ff5-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ff5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ff5-116">См. также</span><span class="sxs-lookup"><span data-stu-id="f9ff5-116">See also</span></span>

- [<span data-ttu-id="f9ff5-117">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f9ff5-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
