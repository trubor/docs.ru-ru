---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Ендинпрокдебуггинг'
title: Метод ICorProfilerInfo::EndInprocDebugging
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: 5e172abaa99e0a64031a9c1ec1beac5f23386d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788622"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="1c745-103">Метод ICorProfilerInfo::EndInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="1c745-103">ICorProfilerInfo::EndInprocDebugging Method</span></span>

<span data-ttu-id="1c745-104">Завершает работу внутрипроцессного сеанса отладки.</span><span class="sxs-lookup"><span data-stu-id="1c745-104">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="1c745-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="1c745-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c745-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c745-106">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c745-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c745-107">Parameters</span></span>  

 `dwProfilerContext`  
 <span data-ttu-id="1c745-108">окне Значение, идентифицирующее сеанс отладки.</span><span class="sxs-lookup"><span data-stu-id="1c745-108">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="1c745-109">Это значение должно совпадать со значением, полученным в методе [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1c745-109">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c745-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c745-110">Remarks</span></span>  

 <span data-ttu-id="1c745-111">Необходимо вызвать метод [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) и в `EndInprocDebugging` том же методе обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="1c745-111">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="1c745-112">Службы отладки CLR поддерживали ограниченную внутрипроцессную отладку в платформа .NET Framework версиях 1,0 и 1,1.</span><span class="sxs-lookup"><span data-stu-id="1c745-112">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="1c745-113">В процессе отладки с помощью профилировщика можно использовать части проверки для API отладки.</span><span class="sxs-lookup"><span data-stu-id="1c745-113">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="1c745-114">Однако из-за отзывов клиентов внутрипроцессный процесс отладки был удален из платформа .NET Framework в версии 2,0 и заменен набором функциональных возможностей, которые более подробно описаны в API профилирования.</span><span class="sxs-lookup"><span data-stu-id="1c745-114">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c745-115">Требования</span><span class="sxs-lookup"><span data-stu-id="1c745-115">Requirements</span></span>  

 <span data-ttu-id="1c745-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c745-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c745-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c745-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c745-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c745-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c745-119">**Версия платформа .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="1c745-119">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c745-120">См. также</span><span class="sxs-lookup"><span data-stu-id="1c745-120">See also</span></span>

- [<span data-ttu-id="1c745-121">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="1c745-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
