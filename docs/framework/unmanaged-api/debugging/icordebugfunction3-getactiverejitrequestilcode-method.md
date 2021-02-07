---
description: 'Дополнительные сведения о методе: ICorDebugFunction3:: GetActiveReJitRequestILCode'
title: Метод ICorDebugFunction3::GetActiveReJitRequestILCode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 9225c5cdf97395b7e1b11c61d653cab8d52031c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692125"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="92f38-103">Метод ICorDebugFunction3::GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="92f38-103">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>

<span data-ttu-id="92f38-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="92f38-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="92f38-105">Возвращает указатель интерфейса на [икордебугилкоде](icordebugilcode-interface.md) , содержащий Il из активного запроса ReJIT.</span><span class="sxs-lookup"><span data-stu-id="92f38-105">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f38-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92f38-106">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92f38-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="92f38-107">Parameters</span></span>  

 `ppReJitedILCode`  
 <span data-ttu-id="92f38-108">Указатель на промежуточный язык из активного запроса ReJIT.</span><span class="sxs-lookup"><span data-stu-id="92f38-108">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92f38-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="92f38-109">Remarks</span></span>  

 <span data-ttu-id="92f38-110">Если метод, представленный этим объектом `ICorDebugFunction3`, имеет активный запрос ReJIT, `ppReJitedILCode` возвращает указатель на его промежуточный язык.</span><span class="sxs-lookup"><span data-stu-id="92f38-110">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="92f38-111">Если нет активного запроса, то есть общего случая, то `ppReJitedILCode` имеет **значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="92f38-111">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="92f38-112">Запрос ReJIT активируется сразу после того, как выполнение возвращается из вызова метода [ICorProfilerCallback4:: жетрежитпараметерс](../profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92f38-112">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="92f38-113">Он еще не быть может скомпилирован JIT, а потоки могут по-прежнему выполняться в исходной версии кода.</span><span class="sxs-lookup"><span data-stu-id="92f38-113">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="92f38-114">Во время вызова профилировщиком метода [метод icorprofilerinfo4:: рекуестреверт](../profiling/icorprofilerinfo4-requestrevert-method.md) запрос ReJIT станет неактивным.</span><span class="sxs-lookup"><span data-stu-id="92f38-114">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="92f38-115">Даже после возврата промежуточного языка поток может все еще выполняться в коде, перекомпилированном JIT (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="92f38-115">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f38-116">Требования</span><span class="sxs-lookup"><span data-stu-id="92f38-116">Requirements</span></span>  

 <span data-ttu-id="92f38-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f38-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f38-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92f38-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92f38-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92f38-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92f38-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f38-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f38-121">См. также</span><span class="sxs-lookup"><span data-stu-id="92f38-121">See also</span></span>

- [<span data-ttu-id="92f38-122">Интерфейс ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="92f38-122">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="92f38-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="92f38-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="92f38-124">ReJIT: руководство по How-To</span><span class="sxs-lookup"><span data-stu-id="92f38-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
