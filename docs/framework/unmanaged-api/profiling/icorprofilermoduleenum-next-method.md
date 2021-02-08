---
description: 'Дополнительные сведения о методе: ICorProfilerModuleEnum:: Next'
title: Метод ICorProfilerModuleEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 06c9528d5468847a905e84fe38591c9b5ef3ee44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798996"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="ec1c5-103">Метод ICorProfilerModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="ec1c5-103">ICorProfilerModuleEnum::Next Method</span></span>

<span data-ttu-id="ec1c5-104">Возвращает заданное число смежных модулей из последовательной коллекции модулей начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-104">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1c5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec1c5-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec1c5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ec1c5-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ec1c5-107">[in] Количество модулей для извлечения.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-107">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="ec1c5-108">[out] Массив значений `ModuleID`, каждое из которых представляет полученный модуль.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-108">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ec1c5-109">[out] Указатель на число элементов, фактически извлеченных в массив `ids`.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-109">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec1c5-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ec1c5-110">Return Value</span></span>  

 <span data-ttu-id="ec1c5-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ec1c5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec1c5-112">HRESULT</span></span>|<span data-ttu-id="ec1c5-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="ec1c5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec1c5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec1c5-114">S_OK</span></span>|<span data-ttu-id="ec1c5-115">Возвращенные элементы `celt`.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="ec1c5-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ec1c5-116">S_FALSE</span></span>|<span data-ttu-id="ec1c5-117">Было возвращено элементов менее, чем `celt`, что указывает, что перечисление завершено.</span><span class="sxs-lookup"><span data-stu-id="ec1c5-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec1c5-118">Требования</span><span class="sxs-lookup"><span data-stu-id="ec1c5-118">Requirements</span></span>  

 <span data-ttu-id="ec1c5-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec1c5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec1c5-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec1c5-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec1c5-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec1c5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec1c5-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec1c5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1c5-123">См. также</span><span class="sxs-lookup"><span data-stu-id="ec1c5-123">See also</span></span>

- [<span data-ttu-id="ec1c5-124">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="ec1c5-124">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="ec1c5-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ec1c5-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
