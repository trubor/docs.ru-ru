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
ms.openlocfilehash: accddef08f3cb76ef2cb1b70993aee24cf83ae50
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760674"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="c5bac-103">Метод ICorProfilerCallback::AssemblyLoadFinished</span><span class="sxs-lookup"><span data-stu-id="c5bac-103">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="c5bac-104">Уведомляет профилировщик о том, что загрузка сборки завершена.</span><span class="sxs-lookup"><span data-stu-id="c5bac-104">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5bac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c5bac-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5bac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c5bac-106">Parameters</span></span>

<span data-ttu-id="c5bac-107">`assemblyId` окне Определяет загруженную сборку.</span><span class="sxs-lookup"><span data-stu-id="c5bac-107">`assemblyId` [in] Identifies the assembly that was loaded.</span></span>

<span data-ttu-id="c5bac-108">`hrStatus` окне Значение HRESULT, указывающее, успешно ли завершена загрузка сборки.</span><span class="sxs-lookup"><span data-stu-id="c5bac-108">`hrStatus` [in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5bac-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c5bac-109">Remarks</span></span>  

 <span data-ttu-id="c5bac-110">Значение недопустимо `assemblyId` для информационного запроса до `AssemblyLoadFinished` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="c5bac-110">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c5bac-111">Некоторые части загрузки сборки могут продолжаться после `AssemblyLoadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="c5bac-111">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="c5bac-112">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="c5bac-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c5bac-113">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть загрузки сборки завершилась успешно.</span><span class="sxs-lookup"><span data-stu-id="c5bac-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5bac-114">Требования</span><span class="sxs-lookup"><span data-stu-id="c5bac-114">Requirements</span></span>  

 <span data-ttu-id="c5bac-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5bac-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5bac-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5bac-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5bac-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5bac-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5bac-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5bac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bac-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c5bac-119">See also</span></span>

- [<span data-ttu-id="c5bac-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c5bac-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
