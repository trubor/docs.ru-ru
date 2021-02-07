---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: SetEventMask'
title: Метод ICorProfilerInfo::SetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
ms.openlocfilehash: e389d25abfecfc9a5dec8834e412fe618324e311
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687198"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="94dc1-103">Метод ICorProfilerInfo::SetEventMask</span><span class="sxs-lookup"><span data-stu-id="94dc1-103">ICorProfilerInfo::SetEventMask Method</span></span>

<span data-ttu-id="94dc1-104">Определяет значение, указывающее типы событий, для которых профилировщик хочет получать уведомления от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="94dc1-104">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94dc1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="94dc1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94dc1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="94dc1-106">Parameters</span></span>  

 `dwEvents`  
 <span data-ttu-id="94dc1-107">[в] 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="94dc1-107">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="94dc1-108">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="94dc1-108">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="94dc1-109">Биты описаны в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="94dc1-109">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94dc1-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="94dc1-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94dc1-111">Вместо этого метода следует вызвать метод [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="94dc1-111">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="94dc1-112">Несмотря на то `SetEventMask` , что метод поддерживается, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) предоставляет дополнительные функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="94dc1-112">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94dc1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="94dc1-113">Requirements</span></span>  

 <span data-ttu-id="94dc1-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94dc1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94dc1-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94dc1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94dc1-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94dc1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94dc1-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94dc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94dc1-118">См. также</span><span class="sxs-lookup"><span data-stu-id="94dc1-118">See also</span></span>

- [<span data-ttu-id="94dc1-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="94dc1-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="94dc1-120">Метод SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="94dc1-120">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
