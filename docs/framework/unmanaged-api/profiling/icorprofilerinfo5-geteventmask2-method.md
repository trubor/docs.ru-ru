---
description: 'Дополнительные сведения о методе: ICorProfilerInfo5:: GetEventMask2'
title: Метод ICorProfilerInfo5::GetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: c6652ffe1b8fd0d99ce5493c8ba27a971363c423
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646664"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="79de4-103">Метод ICorProfilerInfo5::GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="79de4-103">ICorProfilerInfo5::GetEventMask2 Method</span></span>

<span data-ttu-id="79de4-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="79de4-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="79de4-105">Получает текущие категории событий, о которых профилировщик хочет получать уведомления из среды CLR.</span><span class="sxs-lookup"><span data-stu-id="79de4-105">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="79de4-106">Он предоставляет функциональные возможности, не предоставляемые методом [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="79de4-106">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79de4-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="79de4-107">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79de4-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="79de4-108">Parameters</span></span>  

 `pdwEventsLow`  
 <span data-ttu-id="79de4-109">[из] Указатель на 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="79de4-109">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="79de4-110">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="79de4-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="79de4-111">Биты описаны в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="79de4-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="79de4-112">[из] Указатель на 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="79de4-112">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="79de4-113">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="79de4-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="79de4-114">Биты описаны в перечислении [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="79de4-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79de4-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="79de4-115">Remarks</span></span>  

 <span data-ttu-id="79de4-116">Метод `GetEventMask2` используется для определения обратных вызовов, на которые подписался профилировщик.</span><span class="sxs-lookup"><span data-stu-id="79de4-116">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="79de4-117">Обычно выполняется логическое или для `pdwEventsLow` значений и, а также `pdwEventsHigh` все новые биты, которые необходимо задать, а затем вызывается метод [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="79de4-117">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="79de4-118">Этот метод является рекомендуемым альтернативой методу [GetEventMask](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="79de4-118">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79de4-119">Требования</span><span class="sxs-lookup"><span data-stu-id="79de4-119">Requirements</span></span>  

 <span data-ttu-id="79de4-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79de4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79de4-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79de4-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79de4-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79de4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79de4-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79de4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79de4-124">См. также</span><span class="sxs-lookup"><span data-stu-id="79de4-124">See also</span></span>

- [<span data-ttu-id="79de4-125">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="79de4-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="79de4-126">Метод SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="79de4-126">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
