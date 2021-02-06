---
description: 'Дополнительные сведения о методе: ICorDebugILCode2:: GetInstrumentedILMap'
title: Метод ICorDebugILCode2::GetInstrumentedILMap
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 6892b059e1774d7b0a61d7a8dd7df69bc2e8c569
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660574"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="8eeac-103">Метод ICorDebugILCode2::GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="8eeac-103">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>

<span data-ttu-id="8eeac-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="8eeac-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8eeac-105">Возвращает сопоставление смещений инструментированного профилировщиком промежуточного языка со смещениями промежуточного языка исходного метода для этого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="8eeac-105">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eeac-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8eeac-106">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eeac-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="8eeac-107">Parameters</span></span>  

 <span data-ttu-id="8eeac-108">cMap</span><span class="sxs-lookup"><span data-stu-id="8eeac-108">cMap</span></span>  
 <span data-ttu-id="8eeac-109">[в] Емкость хранилища массива `map`.</span><span class="sxs-lookup"><span data-stu-id="8eeac-109">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="8eeac-110">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="8eeac-110">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="8eeac-111">pcMap</span><span class="sxs-lookup"><span data-stu-id="8eeac-111">pcMap</span></span>  
 <span data-ttu-id="8eeac-112">[из] Количество значений COR_IL_MAP, записанных в массив сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="8eeac-112">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="8eeac-113">карта</span><span class="sxs-lookup"><span data-stu-id="8eeac-113">map</span></span>  
 <span data-ttu-id="8eeac-114">[из] Массив значений COR_IL_MAP, предоставляющий информацию о сопоставлениях промежуточного языка, инструментированного профилировщиком, и промежуточного языка исходного метода.</span><span class="sxs-lookup"><span data-stu-id="8eeac-114">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eeac-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="8eeac-115">Remarks</span></span>  

 <span data-ttu-id="8eeac-116">Если профилировщик задает сопоставление путем вызова метода [ICorProfilerInfo:: сетилинструментедкодемап](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , отладчик может вызвать этот метод, чтобы получить сопоставление и использовать внутреннее сопоставление при вычислении смещений Il для трассировок стека и времени существования переменных.</span><span class="sxs-lookup"><span data-stu-id="8eeac-116">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="8eeac-117">Если значение `cMap` равно 0 и `pcMap` не равно **null**, то параметру присваивается `pcMap` число доступных COR_IL_MAP значений.</span><span class="sxs-lookup"><span data-stu-id="8eeac-117">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="8eeac-118">Если значение `cMap` не равно 0, оно обозначает емкость хранилища массива `map`.</span><span class="sxs-lookup"><span data-stu-id="8eeac-118">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="8eeac-119">Когда метод возвращает значение, `map` содержит максимум `cMap` элементов и `pcMap` задается числом COR_IL_MAP значений, фактически записанных в `map` массив.</span><span class="sxs-lookup"><span data-stu-id="8eeac-119">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="8eeac-120">Если промежуточный язык не инструментирован или профилировщик не предоставил сопоставление, этот метод возвращает значение `S_OK` и присваивает `pcMap` значение 0.</span><span class="sxs-lookup"><span data-stu-id="8eeac-120">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eeac-121">Требования</span><span class="sxs-lookup"><span data-stu-id="8eeac-121">Requirements</span></span>  

 <span data-ttu-id="8eeac-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eeac-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eeac-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8eeac-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eeac-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8eeac-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eeac-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eeac-125">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eeac-126">См. также</span><span class="sxs-lookup"><span data-stu-id="8eeac-126">See also</span></span>

- [<span data-ttu-id="8eeac-127">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="8eeac-127">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="8eeac-128">Интерфейс ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="8eeac-128">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="8eeac-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8eeac-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
