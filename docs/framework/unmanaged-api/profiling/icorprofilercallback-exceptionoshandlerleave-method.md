---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионошандлерлеаве'
title: Метод ICorProfilerCallback::ExceptionOSHandlerLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: 809f9440510bc0b55c9cae9827757eb61e61b257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657571"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="a5c28-103">Метод ICorProfilerCallback::ExceptionOSHandlerLeave</span><span class="sxs-lookup"><span data-stu-id="a5c28-103">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="a5c28-104">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="a5c28-104">Not implemented.</span></span> <span data-ttu-id="a5c28-105">Профилировщик, которому требуются сведения о неуправляемом исключении, должен получить эти сведения с помощью других средств.</span><span class="sxs-lookup"><span data-stu-id="a5c28-105">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c28-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5c28-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a5c28-107">Требования</span><span class="sxs-lookup"><span data-stu-id="a5c28-107">Requirements</span></span>  

 <span data-ttu-id="a5c28-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5c28-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c28-109">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5c28-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5c28-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5c28-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5c28-111">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c28-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c28-112">См. также</span><span class="sxs-lookup"><span data-stu-id="a5c28-112">See also</span></span>

- [<span data-ttu-id="a5c28-113">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a5c28-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
