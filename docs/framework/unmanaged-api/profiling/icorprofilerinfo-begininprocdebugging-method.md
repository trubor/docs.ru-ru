---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: BeginInprocDebugging'
title: Метод ICorProfilerInfo::BeginInprocDebugging
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: 151aa3604d61e4c5d9e7e24fe9f17bf754d72233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737406"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="79a16-103">Метод ICorProfilerInfo::BeginInprocDebugging</span><span class="sxs-lookup"><span data-stu-id="79a16-103">ICorProfilerInfo::BeginInprocDebugging Method</span></span>

<span data-ttu-id="79a16-104">Инициализирует поддержку внутрипроцессного отладки.</span><span class="sxs-lookup"><span data-stu-id="79a16-104">Initializes in-process debugging support.</span></span> <span data-ttu-id="79a16-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="79a16-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a16-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="79a16-106">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79a16-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="79a16-107">Parameters</span></span>  

 `fThisThreadOnly`  
 <span data-ttu-id="79a16-108">окне Установите это значение, чтобы `true` инициализировать поддержку отладки только для текущего потока; установите его в значение `false` , чтобы инициализировать поддержку отладки для всех потоков.</span><span class="sxs-lookup"><span data-stu-id="79a16-108">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="79a16-109">заполняет Указатель на возвращаемое значение, идентифицирующее сеанс отладки.</span><span class="sxs-lookup"><span data-stu-id="79a16-109">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79a16-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="79a16-110">Remarks</span></span>  

 <span data-ttu-id="79a16-111">Службы отладки CLR поддерживали ограниченную внутрипроцессную отладку в платформа .NET Framework версиях 1,0 и 1,1.</span><span class="sxs-lookup"><span data-stu-id="79a16-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="79a16-112">В процессе отладки с помощью профилировщика можно использовать части проверки для API отладки.</span><span class="sxs-lookup"><span data-stu-id="79a16-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="79a16-113">Однако из-за отзывов клиентов внутрипроцессный процесс отладки был удален из платформа .NET Framework в версии 2,0 и заменен набором функциональных возможностей, которые более подробно описаны в API профилирования.</span><span class="sxs-lookup"><span data-stu-id="79a16-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a16-114">Требования</span><span class="sxs-lookup"><span data-stu-id="79a16-114">Requirements</span></span>  

 <span data-ttu-id="79a16-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a16-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a16-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79a16-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79a16-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79a16-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79a16-118">**Версия платформа .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="79a16-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a16-119">См. также</span><span class="sxs-lookup"><span data-stu-id="79a16-119">See also</span></span>

- [<span data-ttu-id="79a16-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="79a16-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
