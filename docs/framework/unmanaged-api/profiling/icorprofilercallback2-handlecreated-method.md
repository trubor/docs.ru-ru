---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: Хандлекреатед'
title: Метод ICorProfilerCallback2::HandleCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 17f4ed83646907a229dcc6a30dcce1b52fa608d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657090"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="83607-103">Метод ICorProfilerCallback2::HandleCreated</span><span class="sxs-lookup"><span data-stu-id="83607-103">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="83607-104">Уведомляет профилировщик кода о создании обработчика сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83607-104">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83607-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83607-105">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83607-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="83607-106">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="83607-107">окне Идентификатор обработчика для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83607-107">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="83607-108">окне Идентификатор объекта, для которого был создан маркер сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83607-108">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83607-109">Требования</span><span class="sxs-lookup"><span data-stu-id="83607-109">Requirements</span></span>  

 <span data-ttu-id="83607-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83607-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83607-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83607-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83607-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83607-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83607-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83607-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83607-114">См. также</span><span class="sxs-lookup"><span data-stu-id="83607-114">See also</span></span>

- [<span data-ttu-id="83607-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="83607-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="83607-116">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="83607-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
