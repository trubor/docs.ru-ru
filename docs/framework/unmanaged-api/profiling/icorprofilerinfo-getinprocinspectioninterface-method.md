---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: ЖетинпроЦинспектионинтерфаце'
title: Метод ICorProfilerInfo::GetInprocInspectionInterface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: 5b7ce053f0a64afd5d702a4eb59c1712f4b26e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781471"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="75a62-103">Метод ICorProfilerInfo::GetInprocInspectionInterface</span><span class="sxs-lookup"><span data-stu-id="75a62-103">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>

<span data-ttu-id="75a62-104">Возвращает объект, к которому можно выполнить запрос для интерфейса "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="75a62-104">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="75a62-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="75a62-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a62-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="75a62-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75a62-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="75a62-107">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="75a62-108">[выходной](/cpp/atl/iunknown) объект, к которому можно запросить `ICorDebugProcess` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="75a62-108">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a62-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="75a62-109">Remarks</span></span>  

 <span data-ttu-id="75a62-110">API отладки среды CLR поддерживал ограниченную внутрипроцессную отладку в платформа .NET Framework версии 1,0.</span><span class="sxs-lookup"><span data-stu-id="75a62-110">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="75a62-111">В процессе отладки с помощью профилировщика можно использовать части проверки для API отладки.</span><span class="sxs-lookup"><span data-stu-id="75a62-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="75a62-112">В результате отзывов клиентов внутрипроцессный процесс отладки был удален из платформа .NET Framework в версии 2,0 и заменен набором функциональных возможностей, которые более подробно описаны в API профилирования.</span><span class="sxs-lookup"><span data-stu-id="75a62-112">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75a62-113">Требования</span><span class="sxs-lookup"><span data-stu-id="75a62-113">Requirements</span></span>  

 <span data-ttu-id="75a62-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75a62-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75a62-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75a62-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75a62-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75a62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75a62-117">**Версия платформа .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="75a62-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a62-118">См. также</span><span class="sxs-lookup"><span data-stu-id="75a62-118">See also</span></span>

- [<span data-ttu-id="75a62-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="75a62-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
