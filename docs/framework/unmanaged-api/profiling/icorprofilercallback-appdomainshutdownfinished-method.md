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
ms.openlocfilehash: e08a4f7e03bfd18d9c6a2fdf56bfab8c68f9c379
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648258"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="280aa-103">Метод ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="280aa-103">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="280aa-104">Уведомляет профилировщик о том, что домен приложения был выгружен из процесса.</span><span class="sxs-lookup"><span data-stu-id="280aa-104">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="280aa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="280aa-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="280aa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="280aa-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="280aa-107">\[в] определяет домен, в котором хранятся сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="280aa-107">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="280aa-108">\[in] значение HRESULT, указывающее, успешно ли выгружен домен приложения.</span><span class="sxs-lookup"><span data-stu-id="280aa-108">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="280aa-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="280aa-109">Remarks</span></span>  

 <span data-ttu-id="280aa-110">Значение недопустимо `appDomainId` для информационного запроса после возврата метода [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="280aa-110">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="280aa-111">Некоторые части выгрузки домена приложения могут продолжаться после `AppDomainCreationFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="280aa-111">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="280aa-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="280aa-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="280aa-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает, что первая часть выгрузки домена приложения успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="280aa-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="280aa-114">Требования</span><span class="sxs-lookup"><span data-stu-id="280aa-114">Requirements</span></span>  

 <span data-ttu-id="280aa-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="280aa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="280aa-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="280aa-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="280aa-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="280aa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="280aa-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="280aa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="280aa-119">См. также</span><span class="sxs-lookup"><span data-stu-id="280aa-119">See also</span></span>

- [<span data-ttu-id="280aa-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="280aa-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
