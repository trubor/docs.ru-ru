---
description: 'Дополнительные сведения о методе: ICorProfilerCallback7:: Модулеинмеморисимболсупдатед'
title: 'Метод ICorProfilerCallback7:: Модулеинмеморисимболсупдатед'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 74adf7edc5269824a924933eb3284a5964e1bac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781731"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="40bf9-103">Метод ICorProfilerCallback7:: Модулеинмеморисимболсупдатед</span><span class="sxs-lookup"><span data-stu-id="40bf9-103">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>

<span data-ttu-id="40bf9-104">[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="40bf9-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="40bf9-105">Уведомляет профилировщик каждый раз, когда поток символов, связанный с модулем в памяти, обновляется.</span><span class="sxs-lookup"><span data-stu-id="40bf9-105">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40bf9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40bf9-106">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40bf9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="40bf9-107">Parameters</span></span>  

 <span data-ttu-id="40bf9-108">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="40bf9-108">[in] `moduleId`</span></span>  
 <span data-ttu-id="40bf9-109">Идентификатор модуля в памяти, чей поток символов обновлен.</span><span class="sxs-lookup"><span data-stu-id="40bf9-109">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40bf9-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="40bf9-110">Remarks</span></span>  

 <span data-ttu-id="40bf9-111">Этот обратный вызов управляется путем установки флага [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) маски событий при вызове метода [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40bf9-111">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40bf9-112">Это событие в данный момент не вызывается для неявного создания или изменения символов через <xref:System.Reflection.Emit> API-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="40bf9-112">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="40bf9-113">Даже если символы предоставляются перед вызовом одной из перегрузок управляемых <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> методов, включающих `rawSymbolStore` аргумент для указания символов для сборки, среда выполнения может фактически не связывать символьные данные с модулем до тех пор, пока не будет вызван обратный вызов [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40bf9-113">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="40bf9-114">Это событие предоставляет более позднюю возможность собираются символы для таких модулей.</span><span class="sxs-lookup"><span data-stu-id="40bf9-114">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40bf9-115">Требования</span><span class="sxs-lookup"><span data-stu-id="40bf9-115">Requirements</span></span>  

 <span data-ttu-id="40bf9-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40bf9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40bf9-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40bf9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40bf9-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40bf9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40bf9-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40bf9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40bf9-120">См. также</span><span class="sxs-lookup"><span data-stu-id="40bf9-120">See also</span></span>

- [<span data-ttu-id="40bf9-121">Метод ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="40bf9-121">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="40bf9-122">Метод SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="40bf9-122">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="40bf9-123">Интерфейс ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="40bf9-123">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
