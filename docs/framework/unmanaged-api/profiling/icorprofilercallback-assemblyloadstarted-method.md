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
ms.openlocfilehash: f771008b9aed9322f0c5fd279fa9dfb3086755e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648022"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="91d2d-103">Метод ICorProfilerCallback::AssemblyLoadStarted</span><span class="sxs-lookup"><span data-stu-id="91d2d-103">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>

<span data-ttu-id="91d2d-104">Уведомляет профилировщик о загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="91d2d-104">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d2d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91d2d-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91d2d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="91d2d-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="91d2d-107">\[в] определяет загружаемую сборку.</span><span class="sxs-lookup"><span data-stu-id="91d2d-107">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="91d2d-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="91d2d-108">Remarks</span></span>  

 <span data-ttu-id="91d2d-109">Значение недопустимо `assemblyId` для информационного запроса, пока не будет вызван метод [ICorProfilerCallback:: AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91d2d-109">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d2d-110">Требования</span><span class="sxs-lookup"><span data-stu-id="91d2d-110">Requirements</span></span>  

 <span data-ttu-id="91d2d-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91d2d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91d2d-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91d2d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91d2d-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91d2d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91d2d-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91d2d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d2d-115">См. также</span><span class="sxs-lookup"><span data-stu-id="91d2d-115">See also</span></span>

- [<span data-ttu-id="91d2d-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="91d2d-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
