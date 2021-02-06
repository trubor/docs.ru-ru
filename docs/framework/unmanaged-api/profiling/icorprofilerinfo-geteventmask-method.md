---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetEventMask'
title: Метод ICorProfilerInfo::GetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
ms.openlocfilehash: 8ae02a0ef98330207fa7ce6366342d5e0bcb4f19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647652"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="55156-103">Метод ICorProfilerInfo::GetEventMask</span><span class="sxs-lookup"><span data-stu-id="55156-103">ICorProfilerInfo::GetEventMask Method</span></span>

<span data-ttu-id="55156-104">Получает текущие категории событий, о которых профилировщик хочет получать уведомления из среды CLR.</span><span class="sxs-lookup"><span data-stu-id="55156-104">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55156-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55156-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55156-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="55156-106">Parameters</span></span>  

 `pdwEvents`  
 <span data-ttu-id="55156-107">[из] Указатель на 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="55156-107">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="55156-108">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="55156-108">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="55156-109">Биты описаны в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="55156-109">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55156-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="55156-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55156-111">Вместо этого метода следует вызвать метод [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="55156-111">You should call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="55156-112">Несмотря на то `SetEventMask` , что метод поддерживается, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) предоставляет дополнительные функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="55156-112">Although the `SetEventMask` method continues to be supported, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55156-113">Требования</span><span class="sxs-lookup"><span data-stu-id="55156-113">Requirements</span></span>  

 <span data-ttu-id="55156-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55156-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55156-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55156-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55156-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55156-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55156-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55156-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55156-118">См. также</span><span class="sxs-lookup"><span data-stu-id="55156-118">See also</span></span>

- [<span data-ttu-id="55156-119">Метод GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="55156-119">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="55156-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="55156-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
