---
description: 'Дополнительные сведения о методе: ICorProfilerInfo5:: SetEventMask2'
title: Метод ICorProfilerInfo5::SetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 2928ec408f2fdeb363164530258a3bf5c9719e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799009"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="5adb6-103">Метод ICorProfilerInfo5::SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="5adb6-103">ICorProfilerInfo5::SetEventMask2 Method</span></span>

<span data-ttu-id="5adb6-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="5adb6-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5adb6-105">Определяет значение, указывающее типы событий, для которых профилировщик хочет получать уведомления о событиях от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="5adb6-105">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="5adb6-106">Он предоставляет больше функций, чем метод [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5adb6-106">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5adb6-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5adb6-107">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5adb6-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="5adb6-108">Parameters</span></span>  

 `dwEventsLow`  
 <span data-ttu-id="5adb6-109">[в] 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="5adb6-109">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="5adb6-110">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="5adb6-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="5adb6-111">Биты описаны в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5adb6-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="5adb6-112">[в] 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="5adb6-112">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="5adb6-113">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="5adb6-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="5adb6-114">Биты описаны в перечислении [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5adb6-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5adb6-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="5adb6-115">Remarks</span></span>  

 <span data-ttu-id="5adb6-116">Метод `SetEventMask2` используется для установки обратных вызовов, на которые подписывается профилировщик.</span><span class="sxs-lookup"><span data-stu-id="5adb6-116">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="5adb6-117">Как правило, вызывается метод [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) , чтобы определить, какие биты заданы, ВЫПОЛНЯЮТ логическое или из `pdwEventsLow` его `pdwEventsHigh` значений и любых новых битов, которые необходимо задать, а затем вызовите `SetEventMask2` метод.</span><span class="sxs-lookup"><span data-stu-id="5adb6-117">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="5adb6-118">Этот метод является рекомендуемым альтернативой методу [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5adb6-118">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5adb6-119">Требования</span><span class="sxs-lookup"><span data-stu-id="5adb6-119">Requirements</span></span>  

 <span data-ttu-id="5adb6-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5adb6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5adb6-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5adb6-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5adb6-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5adb6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5adb6-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5adb6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5adb6-124">См. также</span><span class="sxs-lookup"><span data-stu-id="5adb6-124">See also</span></span>

- [<span data-ttu-id="5adb6-125">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="5adb6-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="5adb6-126">Метод GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="5adb6-126">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
