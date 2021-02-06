---
description: 'Дополнительные сведения о методе: Икорпрофилерсреаденум:: NOCOUNT'
title: Метод ICorProfilerThreadEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 5219dfc71b79be82f769ac7c8230beaf62c6f33e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646430"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="60e6b-103">Метод ICorProfilerThreadEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="60e6b-103">ICorProfilerThreadEnum::GetCount Method</span></span>

<span data-ttu-id="60e6b-104">Возвращает число потоков, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="60e6b-104">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60e6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60e6b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="60e6b-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="60e6b-107">заполняет Число потоков, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="60e6b-107">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60e6b-108">Требования</span><span class="sxs-lookup"><span data-stu-id="60e6b-108">Requirements</span></span>  

 <span data-ttu-id="60e6b-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60e6b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60e6b-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60e6b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60e6b-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60e6b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60e6b-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60e6b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e6b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="60e6b-113">See also</span></span>

- [<span data-ttu-id="60e6b-114">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="60e6b-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="60e6b-115">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="60e6b-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
