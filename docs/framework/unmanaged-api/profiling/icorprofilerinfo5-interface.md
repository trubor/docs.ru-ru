---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo5'
title: Интерфейс ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: c89faf3db08adeee3ffcfbb755a5da5ae44b3c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737276"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="92fc9-103">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="92fc9-103">ICorProfilerInfo5 Interface</span></span>

<span data-ttu-id="92fc9-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="92fc9-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="92fc9-105">Подкласс [метод icorprofilerinfo4](icorprofilerinfo4-interface.md) , предоставляющий методы для использования профилировщиками кода для взаимодействия со средой CLR для управления мониторингом событий.</span><span class="sxs-lookup"><span data-stu-id="92fc9-105">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92fc9-106">Методы</span><span class="sxs-lookup"><span data-stu-id="92fc9-106">Methods</span></span>  
  
|<span data-ttu-id="92fc9-107">Метод</span><span class="sxs-lookup"><span data-stu-id="92fc9-107">Method</span></span>|<span data-ttu-id="92fc9-108">Описание</span><span class="sxs-lookup"><span data-stu-id="92fc9-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92fc9-109">Метод GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="92fc9-109">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="92fc9-110">Получает текущие категории событий, о которых профилировщик хочет принимать уведомления из среды CLR.</span><span class="sxs-lookup"><span data-stu-id="92fc9-110">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="92fc9-111">Метод SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="92fc9-111">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="92fc9-112">Определяет значение, указывающее типы событий, для которых профилировщик хочет принимать уведомления о событиях от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="92fc9-112">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92fc9-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="92fc9-113">Remarks</span></span>  

 <span data-ttu-id="92fc9-114">Методы, доступные в этом интерфейсе, предназначены для замены методов [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) и [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92fc9-114">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92fc9-115">Требования</span><span class="sxs-lookup"><span data-stu-id="92fc9-115">Requirements</span></span>  

 <span data-ttu-id="92fc9-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92fc9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92fc9-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92fc9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92fc9-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92fc9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92fc9-119">См. также</span><span class="sxs-lookup"><span data-stu-id="92fc9-119">See also</span></span>

- [<span data-ttu-id="92fc9-120">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="92fc9-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
