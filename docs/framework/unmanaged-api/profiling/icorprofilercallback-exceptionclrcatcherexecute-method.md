---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ExceptionCLRCatcherExecute'
title: Метод ICorProfilerCallback::ExceptionCLRCatcherExecute
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: cb6926fdfcc9b5ffef20cc69c71a3bafefd9f6ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657506"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="43556-103">Метод ICorProfilerCallback::ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="43556-103">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>

<span data-ttu-id="43556-104">Вызывается, когда `catch` блок для исключения выполняется в самой среде CLR.</span><span class="sxs-lookup"><span data-stu-id="43556-104">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="43556-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="43556-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43556-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="43556-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="43556-107">Требования</span><span class="sxs-lookup"><span data-stu-id="43556-107">Requirements</span></span>  

 <span data-ttu-id="43556-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43556-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43556-109">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43556-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43556-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43556-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43556-111">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="43556-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43556-112">См. также</span><span class="sxs-lookup"><span data-stu-id="43556-112">See also</span></span>

- [<span data-ttu-id="43556-113">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="43556-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="43556-114">Метод ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="43556-114">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
