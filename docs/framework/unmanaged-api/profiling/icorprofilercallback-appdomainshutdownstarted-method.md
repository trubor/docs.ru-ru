---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AppDomainShutdownStarted'
title: Метод ICorProfilerCallback::AppDomainShutdownStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 16545142a512ca1c5f4167f61b81ea949e3d14e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648120"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="1c47c-103">Метод ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="1c47c-103">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>

<span data-ttu-id="1c47c-104">Уведомляет профилировщик о том, что домен приложения выгружается из процесса.</span><span class="sxs-lookup"><span data-stu-id="1c47c-104">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c47c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c47c-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c47c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c47c-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="1c47c-107">\[в] определяет домен, в котором хранятся сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="1c47c-107">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c47c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c47c-108">Remarks</span></span>  

 <span data-ttu-id="1c47c-109">Значение недопустимо `appDomainId` для любого запроса информации после `AppDomainShutdownStarted` возврата метода — это последний шанс профилировщика получить сведения об этом домене приложения.</span><span class="sxs-lookup"><span data-stu-id="1c47c-109">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c47c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1c47c-110">Requirements</span></span>  

 <span data-ttu-id="1c47c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c47c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c47c-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c47c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c47c-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c47c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c47c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c47c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c47c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1c47c-115">See also</span></span>

- [<span data-ttu-id="1c47c-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1c47c-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
