---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионклркатчерфаунд'
title: Метод ICorProfilerCallback::ExceptionCLRCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 37027a00e488eed5681b1d99ada6332d59e6a632
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706309"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="f19f8-103">Метод ICorProfilerCallback::ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="f19f8-103">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>

<span data-ttu-id="f19f8-104">Вызывается, когда `catch` блок для исключения обнаруживается в самой среде CLR.</span><span class="sxs-lookup"><span data-stu-id="f19f8-104">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="f19f8-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="f19f8-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f19f8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f19f8-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f19f8-107">Требования</span><span class="sxs-lookup"><span data-stu-id="f19f8-107">Requirements</span></span>  

 <span data-ttu-id="f19f8-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f19f8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f19f8-109">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f19f8-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f19f8-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f19f8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f19f8-111">**Версия платформа .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="f19f8-111">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19f8-112">См. также</span><span class="sxs-lookup"><span data-stu-id="f19f8-112">See also</span></span>

- [<span data-ttu-id="f19f8-113">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f19f8-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f19f8-114">Метод ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="f19f8-114">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
