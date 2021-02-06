---
description: 'Дополнительные сведения о методе: ICorProfilerFunctionEnum:: Skip'
title: Метод ICorProfilerFunctionEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: 6d176c51788135952127008f2f43545ead1e2369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657064"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="2e18b-103">Метод ICorProfilerFunctionEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="2e18b-103">ICorProfilerFunctionEnum::Skip Method</span></span>

<span data-ttu-id="2e18b-104">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="2e18b-104">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e18b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2e18b-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e18b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2e18b-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="2e18b-107">окне Число пропущенных элементов.</span><span class="sxs-lookup"><span data-stu-id="2e18b-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e18b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2e18b-108">Return Value</span></span>  

 <span data-ttu-id="2e18b-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="2e18b-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2e18b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e18b-110">HRESULT</span></span>|<span data-ttu-id="2e18b-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="2e18b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e18b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e18b-112">S_OK</span></span>|<span data-ttu-id="2e18b-113">`celt` элементы пропущены.</span><span class="sxs-lookup"><span data-stu-id="2e18b-113">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="2e18b-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2e18b-114">S_FALSE</span></span>|<span data-ttu-id="2e18b-115">`celt`Пропущено меньше элементов, что означает, что больше нет элементов.</span><span class="sxs-lookup"><span data-stu-id="2e18b-115">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e18b-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="2e18b-116">Remarks</span></span>  

 <span data-ttu-id="2e18b-117">Новая позиции курсора перечислителя — (Текущая позиции) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="2e18b-117">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e18b-118">Требования</span><span class="sxs-lookup"><span data-stu-id="2e18b-118">Requirements</span></span>  

 <span data-ttu-id="2e18b-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e18b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e18b-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e18b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e18b-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e18b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e18b-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e18b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e18b-123">См. также</span><span class="sxs-lookup"><span data-stu-id="2e18b-123">See also</span></span>

- [<span data-ttu-id="2e18b-124">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="2e18b-124">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="2e18b-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="2e18b-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
