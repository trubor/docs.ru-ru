---
description: 'Дополнительные сведения о методе: Икорпрофилерфунктионконтрол:: Сетилинструментедкодемап'
title: Метод ICorProfilerFunctionControl::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: bb345f737459342e0146cbb0e0bd7dd4b1e9a037
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781549"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="83d26-103">Метод ICorProfilerFunctionControl::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="83d26-103">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="83d26-104">Устанавливает карту кода для указанной функции с помощью указанных записей карты языка CIL.</span><span class="sxs-lookup"><span data-stu-id="83d26-104">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d26-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83d26-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83d26-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="83d26-106">Parameters</span></span>  

 `cILMapEntries`  
 <span data-ttu-id="83d26-107">[в] Количество записей в карте.</span><span class="sxs-lookup"><span data-stu-id="83d26-107">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="83d26-108">[в] Массив записей COR_IL_MAP, выделенный вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="83d26-108">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="83d26-109">Интерпретация этих записей такая же, как и для метода [ICorProfilerInfo:: сетилинструментедкодемап](icorprofilerinfo-setilinstrumentedcodemap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83d26-109">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83d26-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="83d26-110">Remarks</span></span>  

 <span data-ttu-id="83d26-111">Установка сопоставления путем вызова этого метода позволяет отладчику получить сопоставление путем вызова [ICorDebugILCode2:: GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="83d26-111">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="83d26-112">Кроме того, он позволяет отладчику использовать сопоставление внутренним образом при вычислении смещений промежуточного языка для трассировок стека и времени существования переменных.</span><span class="sxs-lookup"><span data-stu-id="83d26-112">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d26-113">Требования</span><span class="sxs-lookup"><span data-stu-id="83d26-113">Requirements</span></span>  

 <span data-ttu-id="83d26-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d26-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d26-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83d26-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83d26-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83d26-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83d26-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d26-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d26-118">См. также</span><span class="sxs-lookup"><span data-stu-id="83d26-118">See also</span></span>

- [<span data-ttu-id="83d26-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="83d26-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
