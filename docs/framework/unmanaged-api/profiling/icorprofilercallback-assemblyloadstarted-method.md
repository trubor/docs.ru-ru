---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ассемблилоадстартед'
title: Метод ICorProfilerCallback::AssemblyLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: 19737fc284d49c3690f66e4881450ca5803622e3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760610"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="9a169-103">Метод ICorProfilerCallback::AssemblyLoadStarted</span><span class="sxs-lookup"><span data-stu-id="9a169-103">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>

<span data-ttu-id="9a169-104">Уведомляет профилировщик о загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="9a169-104">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a169-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a169-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a169-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9a169-106">Parameters</span></span>

<span data-ttu-id="9a169-107">`assemblyId` окне Определяет загружаемую сборку.</span><span class="sxs-lookup"><span data-stu-id="9a169-107">`assemblyId` [in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a169-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9a169-108">Remarks</span></span>  

 <span data-ttu-id="9a169-109">Значение недопустимо `assemblyId` для информационного запроса, пока не будет вызван метод [ICorProfilerCallback:: AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a169-109">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a169-110">Требования</span><span class="sxs-lookup"><span data-stu-id="9a169-110">Requirements</span></span>  

 <span data-ttu-id="9a169-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a169-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a169-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a169-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a169-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a169-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a169-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a169-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a169-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9a169-115">See also</span></span>

- [<span data-ttu-id="9a169-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9a169-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
