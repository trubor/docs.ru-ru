---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: ЖетинпроЦинспектионисиссреад'
title: Метод ICorProfilerInfo::GetInprocInspectionIThisThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 07ff904170750976e54e623101a2552db0c7f290
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647249"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="91e03-103">Метод ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="91e03-103">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>

<span data-ttu-id="91e03-104">Возвращает объект, для которого можно запросить интерфейс ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="91e03-104">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="91e03-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="91e03-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e03-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91e03-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91e03-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="91e03-107">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="91e03-108">[выходной](/cpp/atl/iunknown) объект, который можно запросить для `ICorDebugThread` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="91e03-108">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91e03-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="91e03-109">Remarks</span></span>  

 <span data-ttu-id="91e03-110">Службы отладки среды CLR поддерживали ограниченную внутрипроцессную отладку в платформа .NET Framework версии 1,0.</span><span class="sxs-lookup"><span data-stu-id="91e03-110">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="91e03-111">В процессе отладки с помощью профилировщика можно использовать части проверки для API отладки.</span><span class="sxs-lookup"><span data-stu-id="91e03-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="91e03-112">В результате отзывов клиентов внутрипроцессный процесс отладки был удален из платформа .NET Framework в версии 2,0 и заменен набором функциональных возможностей, которые более подробно описаны в API профилирования.</span><span class="sxs-lookup"><span data-stu-id="91e03-112">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91e03-113">Требования</span><span class="sxs-lookup"><span data-stu-id="91e03-113">Requirements</span></span>  

 <span data-ttu-id="91e03-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91e03-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91e03-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91e03-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91e03-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91e03-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91e03-117">**Версия платформа .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="91e03-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e03-118">См. также</span><span class="sxs-lookup"><span data-stu-id="91e03-118">See also</span></span>

- [<span data-ttu-id="91e03-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="91e03-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
