---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AssemblyLoadFinished'
title: Метод ICorProfilerCallback::AssemblyLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 19c0871808455e64ad8a4eb002806a87030f7882
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648042"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="ccf56-103">Метод ICorProfilerCallback::AssemblyLoadFinished</span><span class="sxs-lookup"><span data-stu-id="ccf56-103">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="ccf56-104">Уведомляет профилировщик о том, что загрузка сборки завершена.</span><span class="sxs-lookup"><span data-stu-id="ccf56-104">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ccf56-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccf56-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ccf56-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="ccf56-107">\[в] определяет сборку, которая была загружена.</span><span class="sxs-lookup"><span data-stu-id="ccf56-107">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="ccf56-108">\[in] значение HRESULT, указывающее, успешно ли завершена загрузка сборки.</span><span class="sxs-lookup"><span data-stu-id="ccf56-108">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccf56-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ccf56-109">Remarks</span></span>  

 <span data-ttu-id="ccf56-110">Значение недопустимо `assemblyId` для информационного запроса до `AssemblyLoadFinished` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="ccf56-110">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ccf56-111">Некоторые части загрузки сборки могут продолжаться после `AssemblyLoadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="ccf56-111">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="ccf56-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="ccf56-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ccf56-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть загрузки сборки завершилась успешно.</span><span class="sxs-lookup"><span data-stu-id="ccf56-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccf56-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ccf56-114">Requirements</span></span>  

 <span data-ttu-id="ccf56-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf56-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf56-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ccf56-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ccf56-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccf56-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccf56-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf56-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf56-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ccf56-119">See also</span></span>

- [<span data-ttu-id="ccf56-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ccf56-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
