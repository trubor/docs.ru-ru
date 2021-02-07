---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Житинлининг'
title: Метод ICorProfilerCallback::JITInlining
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 2bd6c48180b9484ef90b6afb505c8171aff57aa4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705646"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="36cfd-103">Метод ICorProfilerCallback::JITInlining</span><span class="sxs-lookup"><span data-stu-id="36cfd-103">ICorProfilerCallback::JITInlining Method</span></span>

<span data-ttu-id="36cfd-104">Уведомляет профилировщик о том, что JIT-компилятор собирается вставить функцию в строку с другой функцией.</span><span class="sxs-lookup"><span data-stu-id="36cfd-104">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36cfd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36cfd-105">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36cfd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="36cfd-106">Parameters</span></span>  

 `callerId`  
 <span data-ttu-id="36cfd-107">окне Идентификатор функции, в которую `calleeId` будет вставлена функция.</span><span class="sxs-lookup"><span data-stu-id="36cfd-107">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="36cfd-108">окне Идентификатор вставляемой функции.</span><span class="sxs-lookup"><span data-stu-id="36cfd-108">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="36cfd-109">[out] `true` значение, чтобы разрешить вставку; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="36cfd-109">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36cfd-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="36cfd-110">Remarks</span></span>  

 <span data-ttu-id="36cfd-111">Профилировщик может задать `pfShouldInline` для значение `false` , чтобы предотвратить `calleeId` вставку функции в `callerId` функцию.</span><span class="sxs-lookup"><span data-stu-id="36cfd-111">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="36cfd-112">Кроме того, профилировщик может глобально отключить встроенную вставку, используя значение COR_PRF_DISABLE_INLINING перечисления [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="36cfd-112">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="36cfd-113">Встроенные функции не вызывают события для входа или вставки.</span><span class="sxs-lookup"><span data-stu-id="36cfd-113">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="36cfd-114">Таким образом, профилировщик должен установить в значение, чтобы `pfShouldInline` `false` получить точную граф вызовов.</span><span class="sxs-lookup"><span data-stu-id="36cfd-114">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="36cfd-115">Установка `pfShouldInline` значения `false` влияет на производительность, так как встроенная вставка обычно увеличивает скорость и сокращает число отдельных событий JIT-компиляции для метода inserted.</span><span class="sxs-lookup"><span data-stu-id="36cfd-115">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36cfd-116">Требования</span><span class="sxs-lookup"><span data-stu-id="36cfd-116">Requirements</span></span>  

 <span data-ttu-id="36cfd-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36cfd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36cfd-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36cfd-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36cfd-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36cfd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36cfd-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36cfd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cfd-121">См. также</span><span class="sxs-lookup"><span data-stu-id="36cfd-121">See also</span></span>

- [<span data-ttu-id="36cfd-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="36cfd-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
