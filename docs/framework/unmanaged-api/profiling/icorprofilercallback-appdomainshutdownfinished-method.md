---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AppDomainShutdownFinished'
title: Метод ICorProfilerCallback::AppDomainShutdownFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 8cd45f73741bd26cb54fa85d7d6a186ebaeab5d8
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760695"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="893a3-103">Метод ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="893a3-103">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="893a3-104">Уведомляет профилировщик о том, что домен приложения был выгружен из процесса.</span><span class="sxs-lookup"><span data-stu-id="893a3-104">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="893a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="893a3-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="893a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="893a3-106">Parameters</span></span>

<span data-ttu-id="893a3-107">`appDomainId` окне Определяет домен, в котором хранятся сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="893a3-107">`appDomainId` [in] Identifies the domain in which the application's assemblies are stored.</span></span>

<span data-ttu-id="893a3-108">`hrStatus` окне Значение HRESULT, указывающее, успешно ли выгружен домен приложения.</span><span class="sxs-lookup"><span data-stu-id="893a3-108">`hrStatus` [in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="893a3-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="893a3-109">Remarks</span></span>  

 <span data-ttu-id="893a3-110">Значение недопустимо `appDomainId` для информационного запроса после возврата метода [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="893a3-110">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="893a3-111">Некоторые части выгрузки домена приложения могут продолжаться после `AppDomainCreationFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="893a3-111">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="893a3-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="893a3-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="893a3-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает, что первая часть выгрузки домена приложения успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="893a3-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="893a3-114">Требования</span><span class="sxs-lookup"><span data-stu-id="893a3-114">Requirements</span></span>  

 <span data-ttu-id="893a3-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="893a3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="893a3-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="893a3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="893a3-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="893a3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="893a3-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="893a3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893a3-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="893a3-119">See also</span></span>

- [<span data-ttu-id="893a3-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="893a3-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
