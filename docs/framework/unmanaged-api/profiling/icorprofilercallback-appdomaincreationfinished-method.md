---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Аппдомаинкреатионфинишед'
title: Метод ICorProfilerCallback::AppDomainCreationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 6995c6cda168b5be5815e6f7b2b4d900ae0d4d67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648367"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="b4685-103">Метод ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="b4685-103">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="b4685-104">Уведомляет профилировщик о том, что домен приложения создан.</span><span class="sxs-lookup"><span data-stu-id="b4685-104">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4685-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4685-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="b4685-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b4685-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="b4685-107">\[в] определяет домен, который был создан.</span><span class="sxs-lookup"><span data-stu-id="b4685-107">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="b4685-108">\[в] значение HRESULT, указывающее, успешно ли создана область приложения.</span><span class="sxs-lookup"><span data-stu-id="b4685-108">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4685-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4685-109">Remarks</span></span>  

 <span data-ttu-id="b4685-110">Идентификатор приложения не является допустимым для запроса информации до `AppDomainCreationFinished` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="b4685-110">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="b4685-111">Некоторые части загрузки домена приложения могут продолжаться после `AppDomainCreationFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="b4685-111">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="b4685-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="b4685-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b4685-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает, что первая часть создания домена приложения успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="b4685-113">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4685-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b4685-114">Requirements</span></span>  

 <span data-ttu-id="b4685-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4685-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4685-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4685-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4685-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4685-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4685-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4685-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4685-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b4685-119">See also</span></span>

- [<span data-ttu-id="b4685-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b4685-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
