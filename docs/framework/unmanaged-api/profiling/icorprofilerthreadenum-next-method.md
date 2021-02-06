---
description: 'Дополнительные сведения о методе: Икорпрофилерсреаденум:: Next'
title: Метод ICorProfilerThreadEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: 74567624cbe5042b8ab63a28e7fb07e9f708a959
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636345"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="49bbc-103">Метод ICorProfilerThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="49bbc-103">ICorProfilerThreadEnum::Next Method</span></span>

<span data-ttu-id="49bbc-104">Возвращает заданное число смежных потоков из упорядоченной коллекции потоков начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="49bbc-104">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49bbc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49bbc-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49bbc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="49bbc-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="49bbc-107">[in] Количество потоков для извлечения.</span><span class="sxs-lookup"><span data-stu-id="49bbc-107">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="49bbc-108">[out] Массив значений `ThreadID`, каждое из которых представляет полученный поток.</span><span class="sxs-lookup"><span data-stu-id="49bbc-108">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="49bbc-109">[out] Указатель на число потоков, фактически извлеченных в массив `ids`.</span><span class="sxs-lookup"><span data-stu-id="49bbc-109">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49bbc-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="49bbc-110">Return Value</span></span>  

 <span data-ttu-id="49bbc-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="49bbc-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="49bbc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49bbc-112">HRESULT</span></span>|<span data-ttu-id="49bbc-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="49bbc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49bbc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="49bbc-114">S_OK</span></span>|<span data-ttu-id="49bbc-115">Возвращенные элементы `celt`.</span><span class="sxs-lookup"><span data-stu-id="49bbc-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="49bbc-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="49bbc-116">S_FALSE</span></span>|<span data-ttu-id="49bbc-117">Было возвращено элементов менее, чем `celt`, что указывает, что перечисление завершено.</span><span class="sxs-lookup"><span data-stu-id="49bbc-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49bbc-118">Требования</span><span class="sxs-lookup"><span data-stu-id="49bbc-118">Requirements</span></span>  

 <span data-ttu-id="49bbc-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49bbc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49bbc-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49bbc-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49bbc-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49bbc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49bbc-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49bbc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bbc-123">См. также</span><span class="sxs-lookup"><span data-stu-id="49bbc-123">See also</span></span>

- [<span data-ttu-id="49bbc-124">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="49bbc-124">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="49bbc-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="49bbc-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
