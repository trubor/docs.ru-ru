---
description: 'Дополнительные сведения о методе: ICorProfilerFunctionEnum:: Next'
title: Метод ICorProfilerFunctionEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: ff525cfa4cc1ea1dee63b8bbd2e37eaf89fc3e74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737523"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="4758a-103">Метод ICorProfilerFunctionEnum::Next</span><span class="sxs-lookup"><span data-stu-id="4758a-103">ICorProfilerFunctionEnum::Next Method</span></span>

<span data-ttu-id="4758a-104">Возвращает заданное число смежных функций из последовательной коллекции функций начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="4758a-104">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4758a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4758a-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4758a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4758a-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="4758a-107">[in] Число извлекаемых функций.</span><span class="sxs-lookup"><span data-stu-id="4758a-107">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="4758a-108">[out] Массив значений `COR_PRF_FUNCTION`, каждое из которых представляет извлеченную функцию.</span><span class="sxs-lookup"><span data-stu-id="4758a-108">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4758a-109">[out] Указатель на число функций, фактически извлеченных в массив `ids`.</span><span class="sxs-lookup"><span data-stu-id="4758a-109">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4758a-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4758a-110">Return Value</span></span>  

 <span data-ttu-id="4758a-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="4758a-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4758a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4758a-112">HRESULT</span></span>|<span data-ttu-id="4758a-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="4758a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4758a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4758a-114">S_OK</span></span>|<span data-ttu-id="4758a-115">Возвращенные элементы `celt`.</span><span class="sxs-lookup"><span data-stu-id="4758a-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="4758a-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4758a-116">S_FALSE</span></span>|<span data-ttu-id="4758a-117">Было возвращено элементов менее, чем `celt`, что указывает, что перечисление завершено.</span><span class="sxs-lookup"><span data-stu-id="4758a-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4758a-118">Требования</span><span class="sxs-lookup"><span data-stu-id="4758a-118">Requirements</span></span>  

 <span data-ttu-id="4758a-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4758a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4758a-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4758a-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4758a-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4758a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4758a-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4758a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4758a-123">См. также</span><span class="sxs-lookup"><span data-stu-id="4758a-123">See also</span></span>

- [<span data-ttu-id="4758a-124">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="4758a-124">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="4758a-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="4758a-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
