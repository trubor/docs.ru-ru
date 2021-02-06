---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AppDomainCreationStarted'
title: Метод ICorProfilerCallback::AppDomainCreationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 00ebbe35f6f4446caeee5ebcd56b853d6e6dc80c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648263"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="7be68-103">Метод ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="7be68-103">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="7be68-104">Уведомляет профилировщик о создании домена приложения.</span><span class="sxs-lookup"><span data-stu-id="7be68-104">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be68-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7be68-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7be68-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7be68-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="7be68-107">\[в] определяет создаваемый домен.</span><span class="sxs-lookup"><span data-stu-id="7be68-107">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="7be68-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="7be68-108">Remarks</span></span>  

 <span data-ttu-id="7be68-109">Идентификатор не является допустимым для запроса информации до вызова метода [ICorProfilerCallback:: аппдомаинкреатионфинишед](icorprofilercallback-appdomaincreationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7be68-109">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be68-110">Требования</span><span class="sxs-lookup"><span data-stu-id="7be68-110">Requirements</span></span>  

 <span data-ttu-id="7be68-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be68-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be68-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7be68-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7be68-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7be68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7be68-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7be68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be68-115">См. также</span><span class="sxs-lookup"><span data-stu-id="7be68-115">See also</span></span>

- [<span data-ttu-id="7be68-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7be68-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
