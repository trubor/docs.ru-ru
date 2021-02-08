---
description: 'Дополнительные сведения о методе: Икорпрофилерфунктионконтрол:: SetILFunctionBody'
title: Метод ICorProfilerFunctionControl::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: 470eefce5b211adcfd111951be9a004b3bd7d8fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781614"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="959b6-103">Метод ICorProfilerFunctionControl::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="959b6-103">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>

<span data-ttu-id="959b6-104">Заменяет тело метода на языке CIL.</span><span class="sxs-lookup"><span data-stu-id="959b6-104">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="959b6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="959b6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="959b6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="959b6-106">Parameters</span></span>  

 `cbNewILMethodHeader`  
 <span data-ttu-id="959b6-107">[in] Общий размер нового кода CIL, включая заголовок и все структуры после тела.</span><span class="sxs-lookup"><span data-stu-id="959b6-107">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="959b6-108">[in] Указатель на новый заголовок на языке CIL.</span><span class="sxs-lookup"><span data-stu-id="959b6-108">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="959b6-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="959b6-109">Return Value</span></span>  

 <span data-ttu-id="959b6-110">Этот метод возвращает следующие специфичные результаты HRESULT.</span><span class="sxs-lookup"><span data-stu-id="959b6-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="959b6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="959b6-111">HRESULT</span></span>|<span data-ttu-id="959b6-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="959b6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="959b6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="959b6-113">S_OK</span></span>|<span data-ttu-id="959b6-114">Замена выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="959b6-114">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="959b6-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="959b6-115">Remarks</span></span>  

 <span data-ttu-id="959b6-116">В отличие от метода [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) `SetILFunctionBody` метод управляет памятью, необходимой для нового тела CIL.</span><span class="sxs-lookup"><span data-stu-id="959b6-116">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="959b6-117">Это означает, что тело CIL, предоставленное профилировщиком, не должно выделяться с помощью интерфейса [IMethodMalloc](imethodmalloc-interface.md) или выделено в определенном диапазоне.</span><span class="sxs-lookup"><span data-stu-id="959b6-117">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="959b6-118">Его можно разместить в любой куче.</span><span class="sxs-lookup"><span data-stu-id="959b6-118">It can be allocated on any heap.</span></span> <span data-ttu-id="959b6-119">Профилировщик может освободить память, используемую для его тела CIL после `SetILFunctionBody` возврата.</span><span class="sxs-lookup"><span data-stu-id="959b6-119">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="959b6-120">Требования</span><span class="sxs-lookup"><span data-stu-id="959b6-120">Requirements</span></span>  

 <span data-ttu-id="959b6-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="959b6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="959b6-122">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="959b6-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="959b6-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="959b6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="959b6-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="959b6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="959b6-125">См. также</span><span class="sxs-lookup"><span data-stu-id="959b6-125">See also</span></span>

- [<span data-ttu-id="959b6-126">Интерфейс ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="959b6-126">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
