---
description: 'Дополнительные сведения о методе: ICorProfilerModuleEnum:: Skip'
title: Метод ICorProfilerModuleEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: 4d814e5e9e369fe286b471fadc9675345cfb5b94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798970"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="be7d1-103">Метод ICorProfilerModuleEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="be7d1-103">ICorProfilerModuleEnum::Skip Method</span></span>

<span data-ttu-id="be7d1-104">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="be7d1-104">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7d1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be7d1-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be7d1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="be7d1-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="be7d1-107">окне Число пропущенных элементов.</span><span class="sxs-lookup"><span data-stu-id="be7d1-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be7d1-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="be7d1-108">Return Value</span></span>  

 <span data-ttu-id="be7d1-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="be7d1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="be7d1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be7d1-110">HRESULT</span></span>|<span data-ttu-id="be7d1-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="be7d1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be7d1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="be7d1-112">S_OK</span></span>|<span data-ttu-id="be7d1-113">`celt` элементы пропущены.</span><span class="sxs-lookup"><span data-stu-id="be7d1-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="be7d1-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="be7d1-114">S_FALSE</span></span>|<span data-ttu-id="be7d1-115">`celt`Пропущено меньше элементов, что означает, что больше нет элементов.</span><span class="sxs-lookup"><span data-stu-id="be7d1-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be7d1-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="be7d1-116">Remarks</span></span>  

 <span data-ttu-id="be7d1-117">Новая позиции курсора перечислителя — (Текущая позиции) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="be7d1-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be7d1-118">Требования</span><span class="sxs-lookup"><span data-stu-id="be7d1-118">Requirements</span></span>  

 <span data-ttu-id="be7d1-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be7d1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be7d1-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be7d1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be7d1-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be7d1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be7d1-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be7d1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7d1-123">См. также</span><span class="sxs-lookup"><span data-stu-id="be7d1-123">See also</span></span>

- [<span data-ttu-id="be7d1-124">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="be7d1-124">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="be7d1-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="be7d1-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
