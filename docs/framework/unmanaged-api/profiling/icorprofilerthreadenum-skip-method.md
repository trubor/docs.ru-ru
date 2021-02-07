---
description: 'Дополнительные сведения о методе: Икорпрофилерсреаденум:: Skip'
title: Метод ICorProfilerThreadEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 1da191980364868ed4237fccaf7495d5417705cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736899"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="867ea-103">Метод ICorProfilerThreadEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="867ea-103">ICorProfilerThreadEnum::Skip Method</span></span>

<span data-ttu-id="867ea-104">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="867ea-104">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="867ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="867ea-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="867ea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="867ea-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="867ea-107">окне Число пропущенных элементов.</span><span class="sxs-lookup"><span data-stu-id="867ea-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="867ea-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="867ea-108">Return Value</span></span>  

 <span data-ttu-id="867ea-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="867ea-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="867ea-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="867ea-110">HRESULT</span></span>|<span data-ttu-id="867ea-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="867ea-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="867ea-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="867ea-112">S_OK</span></span>|<span data-ttu-id="867ea-113">`celt` элементы пропущены.</span><span class="sxs-lookup"><span data-stu-id="867ea-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="867ea-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="867ea-114">S_FALSE</span></span>|<span data-ttu-id="867ea-115">`celt`Пропущено меньше элементов, что означает, что больше нет элементов.</span><span class="sxs-lookup"><span data-stu-id="867ea-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="867ea-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="867ea-116">Remarks</span></span>  

 <span data-ttu-id="867ea-117">Новая позиции курсора перечислителя — (Текущая позиции) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="867ea-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="867ea-118">Требования</span><span class="sxs-lookup"><span data-stu-id="867ea-118">Requirements</span></span>  

 <span data-ttu-id="867ea-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="867ea-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="867ea-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="867ea-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="867ea-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="867ea-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="867ea-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="867ea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867ea-123">См. также</span><span class="sxs-lookup"><span data-stu-id="867ea-123">See also</span></span>

- [<span data-ttu-id="867ea-124">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="867ea-124">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="867ea-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="867ea-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
