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
ms.openlocfilehash: f43997dca1d34b9fbaae34da4dabe2c6d926052c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760617"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="febce-103">Метод ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="febce-103">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>

<span data-ttu-id="febce-104">Уведомляет профилировщик о том, что домен приложения выгружается из процесса.</span><span class="sxs-lookup"><span data-stu-id="febce-104">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="febce-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="febce-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="febce-106">Parameters</span></span>

<span data-ttu-id="febce-107">`appDomainId` окне Определяет домен, в котором хранятся сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="febce-107">`appDomainId` [in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="febce-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="febce-108">Remarks</span></span>  

 <span data-ttu-id="febce-109">Значение недопустимо `appDomainId` для любого запроса информации после `AppDomainShutdownStarted` возврата метода — это последний шанс профилировщика получить сведения об этом домене приложения.</span><span class="sxs-lookup"><span data-stu-id="febce-109">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="febce-110">Требования</span><span class="sxs-lookup"><span data-stu-id="febce-110">Requirements</span></span>  

 <span data-ttu-id="febce-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="febce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="febce-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="febce-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="febce-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="febce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="febce-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="febce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febce-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="febce-115">See also</span></span>

- [<span data-ttu-id="febce-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="febce-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
