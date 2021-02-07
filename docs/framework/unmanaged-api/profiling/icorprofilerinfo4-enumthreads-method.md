---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: EnumThreads'
title: Метод ICorProfilerInfo4::EnumThreads
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d597e68b8765e135d5bdb403dbdb161b7acbaa9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686938"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="5c318-103">Метод ICorProfilerInfo4::EnumThreads</span><span class="sxs-lookup"><span data-stu-id="5c318-103">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="5c318-104">Возвращает перечислитель, предоставляющий методы для последовательного прохода по коллекции всех управляемых потоков в процессе профилирования.</span><span class="sxs-lookup"><span data-stu-id="5c318-104">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c318-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c318-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c318-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5c318-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="5c318-107">заполняет Указатель на интерфейс [икорпрофилерсреаденум](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5c318-107">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c318-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="5c318-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c318-109">Требования</span><span class="sxs-lookup"><span data-stu-id="5c318-109">Requirements</span></span>  

 <span data-ttu-id="5c318-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c318-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c318-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c318-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c318-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c318-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c318-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c318-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c318-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5c318-114">See also</span></span>

- [<span data-ttu-id="5c318-115">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="5c318-115">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="5c318-116">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="5c318-116">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="5c318-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5c318-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5c318-118">Профилирование</span><span class="sxs-lookup"><span data-stu-id="5c318-118">Profiling</span></span>](index.md)
